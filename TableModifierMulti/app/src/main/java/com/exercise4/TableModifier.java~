package com.exercise4;

//OOP Collections
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.util.LinkedHashMap;

//Maven
import com.exercise4.Functions;
import com.exercise4.Validations;

public class TableModifier{
	public static void main(String[] args) throws Exception{
		int rowLength = 0, 
				columnLength = 0;
		
		ArrayList<LinkedHashMap<String,String>> fullMap = new ArrayList<LinkedHashMap<String,String>>();
		
		String fileName = args[0];
		
		columnLength = Functions.readColumnLength(fileName);
		rowLength = Functions.readRowLength(fileName);			
		fullMap = Functions.readFromFile(rowLength,columnLength,fileName);
		
		menu(rowLength,columnLength,fullMap,fileName);
	}	
	
	public static void menuChoices(int rowLength, int columnLength){
		System.out.print("\nRows: " + rowLength + "\tColumns: " + columnLength);
		System.out.println("\n======================================");
		System.out.println("[1] Search");
		System.out.println("[2] Edit");
		System.out.println("[3] Print");
		System.out.println("[4] Reset");
		System.out.println("[5] Add New Row");
		System.out.println("[6] Sort Rows by Key [ASC]");
		System.out.println("[7] Exit");

	}
	
	public static void menu(int rowLength, int columnLength, ArrayList<LinkedHashMap<String,String>> fullMap, String fileName) throws Exception{
		boolean menuInputInvalid = false, switchInputValid = true;	
		int menuChoice = 0;
		int newRowLength = 0;
		
		menuChoices(rowLength, columnLength);		
		
		//OOP
		do{
			do{
				menuInputInvalid = false;
			
				int tempMenuChoice = Validations.isInputMismatch("Menu", "Menu");
				
				menuChoice = tempMenuChoice;
			}while(menuInputInvalid);
			
			switch(menuChoice){
			case 1: //Search	
				fullMap = Functions.readFromFile(rowLength, columnLength, fileName);
				Functions.search(rowLength, columnLength, fullMap);
				display(rowLength, columnLength, fullMap, fileName);
				break;
			case 2: //Edit		
				fullMap = Functions.readFromFile(rowLength, columnLength, fileName);
				fullMap = Functions.edit(rowLength, columnLength, fullMap);
				Functions.writeToFile(fullMap,fileName,rowLength,columnLength);
				display(rowLength, columnLength, fullMap, fileName);
				break;
			case 3:	//Print		
				display(rowLength, columnLength, fullMap, fileName);
				break;
			case 4: //Reset		
				fullMap = Functions.reset("", rowLength, columnLength);
				Functions.writeToFile(fullMap,fileName,rowLength,columnLength);
				display(rowLength, columnLength, fullMap, fileName);
				break;
			case 5: //Add New Row
				fullMap = Functions.readFromFile(rowLength, columnLength, fileName);							
				newRowLength = rowLength + 1;
				fullMap = Functions.addRow(newRowLength, columnLength, fullMap);				
				Functions.writeToFile(fullMap,fileName,newRowLength,columnLength);
				display(newRowLength, columnLength, fullMap, fileName);
				break;
			case 6: // Sort row by key ASC 
				fullMap = Functions.readFromFile(rowLength, columnLength, fileName);
				fullMap = Functions.sort(fullMap, rowLength, columnLength);
				Functions.writeToFile(fullMap,fileName,rowLength,columnLength);
				display(rowLength, columnLength, fullMap, fileName);
				break;
			case 7: //Exit
				System.exit(0);
				break;
			default:
				break;
			}						
			System.out.println();
		}while(switchInputValid);
	}
	
	public static void display(int rowLength, int columnLength, ArrayList<LinkedHashMap<String,String>> fullMap, String fileName) throws Exception{
		columnLength = Functions.readColumnLength(fileName);
		rowLength = Functions.readRowLength(fileName);
		
		fullMap = Functions.readFromFile(rowLength, columnLength, fileName);
		
		Functions.print(rowLength, columnLength, fullMap);
		
		menu(rowLength, columnLength, fullMap, fileName);	
	}
}
