import java.awt.color.ICC_ColorSpace;
import java.nio.file.Path;
import java.util.*;
import java.io.*;

public class shack {

    public BufferedWriter out;
    public String word;
    public File file = new File("C:\\Users\\Anish\\Desktop\\Computer systems lectures\\Assignment 3\\src\\file.shk");// change directory when testing code

    public boolean commands() throws IOException {
        Scanner scanner = new Scanner(System.in);
        shack shack = new shack();
        boolean checkisDec = false;
        boolean checkisCode = false;


        try {
            BufferedReader br = new BufferedReader(new FileReader(file.getName()));

            while ((word = br.readLine()) != null) {
                if (word.contains("//")) {
                    word = word.split("//")[0].trim();
                }

                if(word.startsWith("#") && word.contains(" ") ) {
                    System.err.println("unrecognized input");
                }


                if(word.endsWith("#")){
                    System.err.println("unrecognized input");
                }


                if(word.contains(":") && word.contains(" ")){
                    System.err.println("unrecognized input");
                }

            }
            br.close();

            }
        catch(IOException e){
            System.err.println("unable to read file.shk " + e);
        }
        finally {
            fileChecker();
        }


        return false;

        }


    /**
     *
     * checks if code is true
     */
    public static boolean isUpperCase(String s)
    {
        for (int i=0; i<s.length(); i++)
        {
            if (!Character.isUpperCase(s.charAt(i)))
            {
                return false;
            }
        }
        return true;
    }

    /**
     *
     * checks if it is numeric or not
     */
    public static boolean isNumeric(String strNum) {
        if (strNum == null) {
            return false;
        }
        try {
            double d = Double.parseDouble(strNum);
        } catch (NumberFormatException nfe) {
            return false;
        }
        return true;
    }

    /**
     *
     * converts the file into .asm file and translates the shack language into hack.
     */
    public void fileChecker() throws IOException {
        Scanner sc = new Scanner(file);
        String f1 = file.getName();
        if(!f1.contains(".shk")) {
            throw new FileNotFoundException("Unrecognised file type: ");
        }
        else{
            try {
                if (f1.contains(".shk")) {
                    String s = f1.split(".shk")[0].trim();
                    File f2 = new File(s + ".asm");
                    FileWriter out = new FileWriter(f2.getName());// change directory when testing

                    while (sc.hasNext()) {
                        String w = sc.nextLine();
                        String[] camelCaseWords = w.split("(?=[A-Z])",1);

                        for(String token: camelCaseWords){
                            if(token.matches((".*\\d.*"))){
                                String[] newWord = token.split(" ");
                                try {
                                    if(token.contains("#")) {
                                        int space = token.split(" ").length-1;
                                        if(space == 1) {
                                            String num = newWord[1].replaceAll("#", "");
                                            int n = Integer.parseInt(num);
                                            if (n < 0 || n > 32367) {
                                                System.err.println("unrecognized input ");
                                            }
                                        }
                                        if(space == 2) {
                                            String num = newWord[2].replaceAll("#", "");
                                            int n = Integer.parseInt(num);
                                            if (n < 0 || n > 32367) {
                                                System.err.println("unrecognized input ");
                                            }
                                        }

                                    }
                                    if (token.contains(" ") && !token.contains("#")) {
                                        int space = token.split(" ").length - 1;
                                        if (space == 1) {
                                            String num = newWord[1].replaceAll(" ", "");
                                            int n = Integer.parseInt(num);
                                            if (n < 0 || n > 32367) {
                                                System.err.println("unrecognized input ");
                                            }
                                        }
                                        if(space==2){
                                            String num = newWord[2].replaceAll(" ", "");
                                            int n = Integer.parseInt(num);
                                            if (n < 0 || n > 32367) {
                                                System.err.println("unrecognized input ");
                                            }
                                        }
                                    }

                                }
                                catch (NumberFormatException e){
                                    e.printStackTrace();
                                }
                            }
                            if(token.contains("(?=[A-Z])") && token.length() > 5){
                                System.err.println("illegal opcode");
                            }


                            if(token.contains("ADDD")){
                                if(token.contains("#")){
                                    String[] newWord = token.split("#");
                                    out.write("@" + newWord[1] + "\n"+"D = D + A\n");

                                }
                                if(token.contains(" ") && !token.contains("#")){
                                    String[] newWord = token.split(" ");
                                    out.write("@" + newWord[1] + "\n"+"D = D + M\n");
                                    }
                                }

                           else if(token.contains("ANDD")){
                                if(token.contains("#")){
                                    String[] newWord = token.split("#");
                                    out.write("@" + newWord[1] + "\n"+"D = D & A\n");

                                }
                                if(token.contains(" ") && !token.contains("#")){
                                    String[] newWord = token.split(" ");
                                    out.write("@" + newWord[1] + "\n"+"D = D & M\n");
                                }
                            }
                            else if(token.contains("ORD")){
                                if(token.contains("#")){
                                    String[] newWord = token.split("#");
                                    out.write("@" + newWord[1] + "\n"+"D = D | A\n");

                                }
                                if(token.contains(" ") && !token.contains("#")){
                                    String[] newWord = token.split(" ");
                                    out.write("@" + newWord[2] + "\n"+"D = D | M\n");
                                }
                            }
                            else if(token.contains("SUBD")){
                                if(token.contains("#")){
                                    String[] newWord = token.split("#");
                                    out.write("@" + newWord[1] + "\n"+"D = D - A\n");

                                }
                                if(token.contains(" ") && !token.contains("#")){
                                    String[] newWord = token.split(" ");
                                    out.write("@" + newWord[1] + "\n"+"D = D - M\n");
                                }
                            }
                            else if(token.contains("INC")){
                                out.write("D = D + 1"+"\n");

                            }
                            else if(token.contains("DEC")){
                                out.write("D = D - 1"+"\n");

                            }
                            else if(token.contains("CLR")){
                                out.write("D = 0"+"\n");

                            }
                            else if(token.contains("NEG")){
                                out.write("D = -D"+"\n");

                            }
                            else if(token.contains("NOT")){
                                out.write("D = !D"+"\n");

                            }
                            else if(token.contains("STO")){
                                if(!token.contains(" ")){
                                    System.err.println("illegal operand");
                                }

                                if(token.contains("A")){
                                    String[] newWord = token.split(" ");
                                    out.write("D = A\n" + "@"+newWord[2] + "\n"+"M = D\n");
                                }
                                if(token.contains("D")){
                                    String[] newWord = token.split(" ");
                                    out.write("@"+newWord[2]+"\nM = D\n");
                                }

                            }
                            else if(token.contains("LOAD")) {
                                String[] newWord = token.split(" ");
                                int space = token.split(" ").length-1;
                                if (newWord[1].equals("D") || newWord[1].equals("A")) {
                                    if (newWord[1].equals("D") && newWord[2].equals("A")) {
                                        out.write("D = A\n");
                                    }
                                    if (newWord[1].equals("A") && newWord[2].equals("D")) {
                                        out.write("A = D\n");
                                    }
                                    if (newWord[1].equals("A") && newWord[2].startsWith("#")) {
                                        String wo = newWord[2].replaceAll("#", "");
                                        out.write("@" + wo + "\n");
                                    }
                                    if (newWord[1].equals("A") && shack.isNumeric(newWord[2])) {
                                        out.write("@" + newWord[2] + "\nA = M\n");
                                    }
                                    if (newWord[1].equals("D") && newWord[2].contains("#")) {
                                        String wo = newWord[2].replaceAll("#", "");
                                        out.write("D = A\n" + "@R13\n" + "M = D\n" + "@" + wo + "\nD = A\n" + "@R13\n" + "A = M\n");
                                    }
                                    if (newWord[1].equals("D") && !newWord[2].contains("#") && !newWord[2].equals("A")) {
                                        String wo = newWord[2].replaceAll("#", "");
                                        out.write("D = A\n" + "@R13\n" + "M = D\n" + "@" + wo + "\nD = M\n" + "@R13\n" + "A = M\n");

                                    }

                                }
                            }
                            else if(token.contains("JMP")){
                                String[] newWord = token.split(" ");
                                if(newWord[0].contains("#") || newWord[1].equals("#")){
                                    System.err.println("Illegal operand: "+newWord[1]);
                                }
                                if(!newWord[0].contains("#") && !newWord[1].equals("#") && !shack.isUpperCase(newWord[1])){
                                    out.write("@"+newWord[1]+"\n0; JMP\n");
                                }

                            }
                            else if(token.contains("JGT")){
                                String[] newWord = token.split(" ");
                                if(newWord[0].contains("#") || newWord[1].equals("#")){
                                    System.err.println("Illegal operand: "+newWord[1]);
                                }
                                if(!newWord[0].contains("#") && !newWord[1].equals("#") && !shack.isUpperCase(newWord[1])){
                                    out.write("@"+newWord[1]+"\nD; JGT\n");
                                }
                            }
                            else if(token.contains("JEQ")){
                                String[] newWord = token.split(" ");
                                if(newWord[0].contains("#") || newWord[1].equals("#")){
                                    System.err.println("Illegal operand: "+newWord[1]);
                                }
                                if(!newWord[0].contains("#") && !newWord[1].equals("#") && !shack.isUpperCase(newWord[1])){
                                    out.write("@"+newWord[1]+"\nD; JEQ\n");
                                }
                            }
                            else if(token.contains("JGE")){
                                String[] newWord = token.split(" ");
                                if(newWord[0].contains("#") || newWord[1].equals("#")){
                                    System.err.println("Illegal operand: "+newWord[1]);
                                }
                                if(!newWord[0].contains("#") && !newWord[1].equals("#") && !shack.isUpperCase(newWord[1])){
                                    out.write("@"+newWord[1]+"\nD; JGE\n");
                                }
                            }
                            else if(token.contains("JLT")){
                                String[] newWord = token.split(" ");
                                if(newWord[0].contains("#") || newWord[1].equals("#")){
                                    System.err.println("Illegal operand: "+newWord[1]);
                                }
                                if(!newWord[0].contains("#") && !newWord[1].equals("#") && !shack.isUpperCase(newWord[1])){
                                    out.write("@"+newWord[1]+"\nD; JLT\n");
                                }
                            }
                            else if(token.contains("JNE")){
                                String[] newWord = token.split(" ");
                                if(newWord[0].contains("#") || newWord[1].equals("#")){
                                    System.err.println("Illegal operand: "+newWord[1]);
                                }
                                if(!newWord[0].contains("#") && !newWord[1].equals("#") && !shack.isUpperCase(newWord[1])){
                                    out.write("@"+newWord[1]+"\nD; JNE\n");
                                }
                            }
                            else if(token.contains("JLE")){
                                String[] newWord = token.split(" ");
                                if(newWord[0].contains("#") || newWord[1].equals("#")){
                                    System.err.println("Illegal operand: "+newWord[1]);
                                }
                                if(!newWord[0].contains("#") && !newWord[1].equals("#") && !shack.isUpperCase(newWord[1])){
                                    out.write("@"+newWord[1]+"\nD; JLE\n");
                                }
                            }

                        }

                    }
                    out.close();
                }

            }
            catch (Exception e){
                System.err.println(e);
            }

        }


    }

    /**
     *
     * checks if the file is .shk 
     */

    public static void main(String args[]) {
        if (args.length != 1) {
            System.err.println("Usage: java Main file.shk");
        } else {
            String filename = args[0];
            if (filename.endsWith(".shk")) {
                try {
                    shack shack = new shack();
                    shack.commands();

                } catch (Exception e) {
                    System.err.println("Exception parsing: " + filename);
                    System.err.println(e);
                }
            } else {
                System.err.println("Unrecognised file type: " + filename);
            }
        }
    }
}
