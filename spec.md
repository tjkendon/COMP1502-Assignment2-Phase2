# COMP 1502 Assignment 2 - Phase 2

Date Given: **February 20, 2018**
Date Due: 
* Full Solution : **March 9, 2018** - Midnight - Uploaded to your Assignment 2 Phase 2 GitHub Repository (that's this one!)

## Overview

In Phase 1, we developed a system to process inventory transactions and customer orders on-line.  In this phase, we will *enhance* our program to enable to maintain the inventory in stock by adding or removing inventory items.  We shall also change the processing of transactions from an on-line system to processing transactions that were saved into the file (batch processing).  

## Outcomes

* to continue to develop classses using the Best Software Practices guidelines
* to implement and test dynamic collections
* to enhance existing code to reflect additional requirements (software maintenance)

## Updated Functional Requirements

1. The Warehouse class

   We want to replace the array of itmes with a more dynamic collection.

   1. Replace Array with ArrayList<Item>

      The Warehouse class created an array of Items.  However, because inventory items change often through addition and removal of items, an array implementation will severely limit the maintenance of these items.  Hence, Warehouse should implement lists instead.  

      The first step is to replace the array implementation with an ArrayList implementation This would mean changing any statement that use an array processing to ArrayList processing.  

   The following four methods are used for inventory maintenance.

   1. loadData method

      In phase 1, the data is hardcoded.   In this phase, you will replace the contents of this method by loading data from an input file.  The method will receive the filename as an argument.  

      An input file “Inventory.txt” is provided for you.  The contents of this file is exactly the same as the hardcoded data from Phase 1.   You may use this file or you may create one of your own.  Just make sure that you have enough data in the line as in the hardcoded data.

      You may need to change the constructor to reflect this new requirement.

   1. Create an add Item method

      New inventory items are often added to the warehouse stock.  This method will enable the addition of new items.  

      In order to add a new item, the item number is entered and validated.  If the item number is valid, then the item cannot be added and the user is informed of this situation.

      If the item is not valid, a new item with that item number is created and added to the list.  All instance variables except for committed and onOrder are inputted via the terminal window.  

   1. Create a remove Item method

      Items are also removed from inventory.  To remove an item, the item number is entered and validated.   If the item number is valid, then the item with that item number is removed. 

      If it is not valid, nothing can be done and then the user is informed of the situation.

   1. Create a change Item price method

      The unit price of an item can also change.  To change the price of an item, the item number is entered and validated.   If the item number is valid, then the new unit price is entered and used to update the appropriate variable of the Item with that item number.

      If it is not valid, nothing can be done and the user is informed of the situation.

      Note:  in this scenario, changing the price of the item will change the cost of the materials that are in committed.   In reality, the change of price should only affect the onHand items.  However, for the purposes of this assignment, this is a complexity that we will not include.

   1. Create a process transaction file method

      The transactions are saved in a text file “transaction.txt”, also included.  Each transaction is in a line containing three data items: the Item number, the transaction type and the amount.  The transaction type is the same as those in phase 1 options 2 to 7.  

      Each transaction is read. In addition to validating the item number, the transaction type is also validated.  If everything is valid, then appropriate processing is performed as in Phase 1.  The only difference between Phase 1 and Phase 2 is that in Phase 1, the transactions are entered on-line while in Phase 2, the transactions are located in a file.

   1. At the end of processing the transactions, your will need to save the new Item data into a file.  This saved file will be used the next time you run the Inventory Processing Sysgtem.  Therefore, either add saving the Item data to the End of the Day processing or before completely shutting down the system, option 5 below, save the data into a file.  The format of the data should be the same as the format of the input file that you used.

      As a final test, use this saved file as input and run your system again. You can use the same transaction file.   

2. A new interface

   You will receive the starting point for the Client Interface class.  It contains the menu systems as shown below:

   ```
   MAIN MENU:
   1) Inventory item inquiry
   2) Warehouse and Inventory Maintenance        
   3) Process transactions from the file        
   4) End of Day Processing
   5) Exit
   ```

   Options 1 and 4 of the MAIN MENU  are the same as in Phase 1.  Option 2 calls the Inventory Maintenance Options which will show a INVENTORY MAINTENANCE MENU sub-menu as shown below. Option 3 will allow your program to processes transactions which is discussed in a moment.

   ```
   INVENTORY MAINTENANCE MENU:
   1) Adding an Item to the Warehouse
   2) Removing an Item from the Warehouse
   3) Changing the price of an Item in the Warehouse
   4) Back
   ```
   
   To process transctions you will need to perform behaviours 2 - 7 from phase 1. One major difference, in this phase, the transactions are located in a transaction file. You will have to read this file and handle each transaction. 
   
   **Note: You may hard code the transaction filename. Assume that the data is clean, that is, it does not contain data that will “crash” the system.  However, it might contain data that may be erroneous such as non-existent inventory number.**
   
   A sample transaction file is included in the Start folder, however, it contain only 2 transactions.  You will need to create more transactions to completely test your program.  The Test run document that was included in the marking of your Phase 1 should provide some guide.
  
   As each transaction (in the file) is processed, a statement of what happened should be printed on the terminal window.  If the transaction is valid, details of the transaction should be printed (this should have been included in phase 1).  If not valid, the reason should be printed out (invalid item number or invalid transaction code).  

   You should not need to touch the code for the Warehouse class methods developed in Phase 1. For the Inventory Maintenance options, the appropriate Warehouse method is called.   You will need to develop these methods.


## Programming / Testing Requirements

Your code should be stylish, consistant, and easy to read. Your classes and methods should be coherent (focused on one thing). Your names should be descriptive. Use class members and instance members appropriately. Use whitespace liberally and to good effect.

Your code should be documented well. Documentation should describe the purpose and function of each class and method, how it should be used, and any caviates to be aware of. Method documentation should include what input is required, and what values will be returned.

## Testing

Our transaction file does not cover all of the potential transactions. Your transaction file should. While you do not have to complete a hand written solution to this phase of the assignment you should produce a test plan that lists all of the potential transactions your system will see (both valid and invalid). Use this to determine what you want to include in your transaction file.

## Development Suggestions

This is a large, more complex program than you have done so far. Expect it to take longer that you might anticipate.

Develop your solution one bit at a time – **never design, code and test a large program in its entirety**. As you write each new method, test it, by writing a test driver, or by calling one of the Warehouse methods from the Interface.  

A suggestion might be to delay the reading of the inventory file to the end.  Use the same hardcoded data as in Phase 1 and create the Item objects and load into the ArrayList.  When all your other methods are working to your satisfaction, you can change the load data method to read the input file and populate the ArrayList.  This way, you do not get hung up on loading the file and sacrifice the rest of the program.  Writing to the file should be the last process you should develop and test.


