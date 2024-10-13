Project Description :
//
This is a project that efficiently manages a phonebook that is able to update, delete, search, insert, display all and sort contacts accordingly to the user and will. 
Using the following modules and with their functions:

1. Insertion of a contact : client (user) will insert new contacts and keep them stored in the Phonebook of their mobile devices.

2.	Search Contact: client (user) will be able to search for contacts throughout the phonebook using linear Stack apllications

4.	Display Contact: client (user) will be to display all contacts in their phonebook

5.	Deletion Contact: client (user) will be able to delete any contact wished in their phonebook

6.	Update Contact: client (user) can update by means of adding more information to the desired contact they wish or remove information desired

7.	 Sort Contacts: client (user) can arrange their contacts into their desired arrangement they wish by example of either sorting in alphabetical order or time user inserted their contacts etc.

//
# DSA CODING:
package DSA;

import java.util.ArrayList;

import java.util.Collections;

import java.util.Comparator;

import java.util.Scanner;



class Contact {

    String name;

    String number;



    Contact(String name, String number) {

        this.name = name;

        this.number = number;

    }



    @Override

    public String toString() {

        return "Name: " + name + ", Number: " + number;

    }

}



public class Phonebook {

    private ArrayList<Contact> contacts = new ArrayList<>();

    private Scanner scanner = new Scanner(System.in);



    // Insert Contact

    public void insertContact() {

        System.out.print("Enter name: ");

        String name = scanner.nextLine();

        System.out.print("Enter number: ");

        String number = scanner.nextLine();



        if (number.length() > 10) {

            System.out.println("Number does not exist.");

        } else if (number.length() == 10) {

            contacts.add(new Contact(name, number));

            System.out.println("Number is added.");

        }

    }



    // Search Contact

    public void searchContact() {

        System.out.print("Enter number to search: ");

        String searchNumber = scanner.nextLine();



        long startTime = System.nanoTime();



        for (Contact contact : contacts) {

            if (contact.number.equals(searchNumber)) {

                System.out.println("Found: " + contact);

                long endTime = System.nanoTime();

                System.out.println("Search time: " + (endTime - startTime) + " ns");

                return;

            }

        }



        long endTime = System.nanoTime();

        System.out.println("Contact not found. Search time: " + (endTime - startTime) + " ns");

    }



    // Display All Contacts

    public void displayContacts() {

        if (contacts.isEmpty()) {

            System.out.println("Phonebook is empty.");

            return;

        }



        for (Contact contact : contacts) {

            System.out.println(contact);

        }

    }



    // Delete Contact

    public void deleteContact() {

        System.out.print("Enter number to delete: ");

        String deleteNumber = scanner.nextLine();



        for (int i = 0; i < contacts.size(); i++) {

            if (contacts.get(i).number.equals(deleteNumber)) {

                System.out.println("The deleted number is: " + contacts.get(i).number);

                contacts.remove(i);

                return;

            }

        }



        System.out.println("Phonebook is empty or contact not found.");

    }



    // Update Contact

    public void updateContact() {

        System.out.print("Enter number to update: ");

        String updateNumber = scanner.nextLine();



        for (Contact contact : contacts) {

            if (contact.number.equals(updateNumber)) {

                System.out.print("Enter new name: ");

                String newName = scanner.nextLine();

                contact.name = newName; // Update name

                System.out.println("Contact is updated.");

                return;

            }

        }



        System.out.println("Phonebook is empty or contact not found.");

    }



    // Sort Contacts

    public void sortContacts() {

        Collections.sort(contacts, Comparator.comparing(c -> c.number));

        System.out.println("Contacts sorted successfully.");

    }



    public static void main(String[] args) {

        Phonebook phonebook = new Phonebook();



        while (true) {

            System.out.println("\n1. Insert Contact");

            System.out.println("2. Search Contact");

            System.out.println("3. Display All Contacts");

            System.out.println("4. Delete Contact");

            System.out.println("5. Update Contact");

            System.out.println("6. Sort Contacts");

            System.out.println("7. Exit");

            System.out.print("Choose an option: ");



            int choice = phonebook.scanner.nextInt();

            phonebook.scanner.nextLine(); // Consume newline



            switch (choice) {

                case 1:

                    phonebook.insertContact();

                    break;

                case 2:

                    phonebook.searchContact();

                    break;

                case 3:

                    phonebook.displayContacts();

                    break;

                case 4:

                    phonebook.deleteContact();

                    break;

                case 5:

                    phonebook.updateContact();

                    break;

                case 6:

                    phonebook.sortContacts();

                    break;

                case 7:

                    System.exit(0);

                    break;

                default:

                    System.out.println("Invalid option. Please try again.");

            }

        }

    }

}



 
