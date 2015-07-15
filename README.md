# powersports-parts-to-bigcommerce

Overview:

This program will accept CSV files full of part numbers as input, for example a file like
    
    56-1593, 1239-1098, 21-204C, 90382197, DS12409

It will analyze each part number and determine which distributor to pull data from based on the structure of the number. For example, all 8-digit part numbers with no dashes, 8 digit part numbers with a dash between the two sets of four, and part numbers starting with the characters 'DS' are Parts Unlimited part numbers. All part numbers starting with two digits and followed by a dash and then three or four or five digits are Western Powersports part numbers.

It will then create bigcommerce products with the descriptions, prices, and images from each distributors databases.

Alternatively, we could require the end user to specify which distributor they would like the program to query, and only feed it CSV files with one distributor's part numbers at a time.

It will periodically check the databases of each distributor for price, image, description, and availability changes, and update the bigcommerce site based on that information. 

It should have a GUI that is very simple and easy to use. Simply click "browse," select your CSV file, if necessary specify which distributor, enter the required credentials, such as the credentials to access the distributor's data and the credentials for the bigcommerce store you want to load parts into, and click "Create Products."

This program should run on windows as an executable. However, the "back-end" can be running on a VPS, hosting the databases needed and doing the actual querying of the distributors.
