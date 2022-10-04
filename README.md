# File-Reader
/*
date: Feb 25, 2021
author: Asumi 
purpose: This program is to perform some operations on the text file of the user's choice. 
*/

import java.util.Scanner;
import java.io.*;
class OperateFile{
    public void CountWords(){
        try{
            File file = new File("e:\\java\\file.txt"); //I could not use c file, so I used e file.
            
            if(file.exists()){
                
            }
            String[] words = null;  
            int count = 0;     
            FileReader fr = new FileReader(file);    
            BufferedReader br = new BufferedReader(fr);   
            String s;
            
            while((s = br.readLine()) != null){
                words = s.split(" ");   
                count += words.length;   
            }
            fr.close();
            
            
            System.out.println("Number of words in the file is " + count);  
            
              
        }catch (IOException ex){
            System.out.println("There is a problem.");
        }

    }
    
    public void CountCharacters(){
        try{
            File file = new File("e:\\java\\file.txt"); //I could not use c file, so I used e file.
            
            if(file.exists()){
                
            }
            String[] words = null;  
            int count = 0; 
            int Characount = 0;
            FileReader fr = new FileReader(file);    
            BufferedReader br = new BufferedReader(fr);   
            String s;
            
            while((s = br.readLine()) != null){   
                    words = s.split(" ");   
                    count += words.length;   
                    Characount += s.length(); 
            }
            fr.close();
            
            
            System.out.println("Number of characters in the file is " +(Characount-(count-1)));  
            
              
        }catch (IOException ex){
            System.out.println("There is a problem.");
        }
        
    }
    
    public void RemoveAll(){
        String para = null;
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        
        try{   
            System.out.print("Which line do you want to delete?");
            para = br.readLine();
            
            File file = new File("e:\\java\\file.txt"); //I could not use c file, so I used e file
            
            String s = null;
            
            if ( !file.exists() ) {
            System.out.println( "No file exists." );
            }
            
            int para1 = Integer.parseInt(para);
            fileRead(file, para1);
                  
        }catch (IOException ex){
            System.out.println("There is a problem.");
        }                     
    } 
 
    public void ReplaceAll(){
        String para = null;
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        try{
            System.out.print("Please put the word you want to write:");
            para = br.readLine();
            
            File file = new File("c:\\java\\file.txt" );

             if ( !file.exists() ) {
                System.out.println( "No file exists." );
            }

            if ( !file.canWrite() ) {
                System.out.println("Impossible to read the file.");
            }

            int para1 = Integer.parseInt( para );
            fileRead(file, para1);
            fileWrite(file, para);
        
        }catch (IOException ex){
            System.out.println("There is a problem.");
        }
    }

    private static String fileRead(File file, int para) {

        StringBuffer fileRead = new StringBuffer("");

        try {
            FileReader fr = new FileReader(file);
            BufferedReader br = new BufferedReader( fr );
            
            String s = null;
            int count = 1;
            
            while ( ( s = br.readLine() ) != null ) {
                if ( count != para) {
                    fileRead.append(s);
                } else {
                    System.out.println( "Delete: "+s );
                }
                count++;
            }
            br.close();

        } catch ( FileNotFoundException ex ) {
             System.out.println( ex );
        } catch ( IOException ex ) {
             System.out.println( ex );
        }
        return fileRead.toString();
    }

    private static void fileWrite(File file, String s){

        try {
            FileWriter fWriter = new FileWriter(file);
            fWriter.write(s);
            fWriter.close();

        } catch ( IOException ex ) {
             System.out.println( ex );
        }
    }   
}

public class FileReader {
    public static void main(String[] args) throws IOException{
        Scanner input = new Scanner(System.in); 
        OperateFile f1 = new OperateFile(); 

        int res;
            do { 
            
                System.out.println();
                System.out.println("1. Count the number of words in the file.");
                System.out.println("2. Count the number of characters in the file.");
                System.out.println("3. Remove all occurrences of a word from the file.");
                System.out.println("4. Replace all occurrences of a word in the file with another\n" +
                                    "word.");
                System.out.println("5. Exit.");
            
                System.out.println("Enter a choice: ");
                res = input.nextInt();
                input.nextLine();
                if (res == 1) {
                    f1.CountWords();
                    System.out.println();
                
                }else if (res == 2) {
                    f1.CountCharacters();
                    
                    System.out.println();
                
                }else if(res == 3){
                    f1.RemoveAll();
                    
                    System.out.println();

                }else if(res == 4){
                    f1.ReplaceAll();

                    System.out.println();

                }  
            }while (res !=0 && res !=5); 
  
            System.out.println("Good Bye!");
    }    
            

}
