# powersports-parts-to-bigcommerce

**Overview:**

This program will accept CSV files full of part numbers as input, for example a file like
    
    56-1593, 1239-1098, 21-204C, 90382197, DS12409

It will analyze each part number and determine which distributor to pull data from based on the structure of the number. For example, all 8-digit part numbers with no dashes, 8 digit part numbers with a dash between the two sets of four, and part numbers starting with the characters 'DS' are Parts Unlimited part numbers. All part numbers starting with two digits and followed by a dash and then three or four or five digits are Western Powersports part numbers.

It will then create bigcommerce products with the descriptions, prices, and images from each distributors databases.

Alternatively, we could require the end user to specify which distributor they would like the program to query, and only feed it CSV files with one distributor's part numbers at a time.

It will periodically check the databases of each distributor for price, image, description, and availability changes, and update the bigcommerce site based on that information. 

It should have a GUI that is very simple and easy to use. Simply click "browse," select your CSV file, if necessary specify which distributor, enter the required credentials, such as the credentials to access the distributor's data and the credentials for the bigcommerce store you want to load parts into, and click "Create Products."

This program should run on windows as an executable. However, the "back-end" can be running on a VPS, hosting the databases needed and doing the actual querying of the distributors.

**Bounties:**

We need the following tasks to be completed and are willing to pay the following amounts (via paypal or bitcoin). They are presented below in order of urgency, with the most urgent tasks first:

1. Write the primary P.U. to bigcommerce script. Offering $120.
    * Write a new script which will take Parts Unlimited part numbers as input and make bigcommerce products as output. 
    * The script will need to query our mysql database which contains all the data that Parts Unlimited has made available to us so far. This database is already there, and we have an example script (https://github.com/151henry151/parts-unlimited-to-bigcommerce/blob/master/python_scripts/pull_from_database.py) that demonstrates how to access the data. 
    * Then the script will need to interact with the bigcommerce API (https://developer.bigcommerce.com/api/) to create the product with the data that it pulled from the mysql database. We have a script that puts products on to bigcommerce already, so you have an example to look to for this aspect as well.
    * https://github.com/151henry151/wps-to-bigcommerce - This script is the example script for how to put products onto the e-commerce site using the bigcommerce API. However, there's a catch. It uses the requests module directly, instead of using the bigcommerce API python wrapper (https://github.com/bigcommerce-api-python). For that reason, it might not be the best example script. However, it works, so if you'd rather use the requests module directly in the new script as well, that would probably be fine. Whatever works.
    * 
2. Fix the broken WPS script. Offering $60.
    * Modify an existing script (https://github.com/151henry151/wps-to-bigcommerce) which was working, and which builds bigcommerce products using data pulled from the WPS API (it's the example script mentioned above), but which stopped working when WPS changed over to their new API V2 and discontinued support for the old API.

3. Write an updater script. Offering $75.
    * Write a script which will update our bigcommerce products with fresh data from our distributors. This script will need to check the bigcommerce products for consistency with the most current distributor data. There are more details on the updater project at https://github.com/151henry151/parts-unlimited-to-bigcommerce/blob/master/updater_ideas.md

4. Create the windows interface. Offering $150.
    * Write a windows executable that will allow the end user to work with the other scripts. This readme describes it in an earlier section.
