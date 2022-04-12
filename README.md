# Web-scrapping-corona-data-into-excel
What is Web Scrapping?
If you’ve ever copy and pasted information from a website, you’ve performed the same function as any web scraper, only on a microscopic, manual scale. Web scraping, also known as online data mining, is the method of extracting or scraping data from a website. This knowledge is gathered and then translated to a medium that is more accessible to the user. It’s either a spreadsheet or an API.

Approach: 

Request for a response from the webpage.
Parse and extract with the help of the BeautifulSoup() class method and lxml module.
Download and export the data with pandas into Excel.
The Data Source:

We need a webpage to fetch the coronavirus data. So we will be using the Worldometer website here. Worldometer’s webpage will look something like this:


data source 

Programmatic Implementation
There are a few libraries you will need, so first, you need to install them.

Go to your command line and install them.

pip install requests
pip install lxml
pip install bs4
Now let’s see what we can do with these libraries.

Below are the steps for Web Scraping Coronavirus Data into Excel:

Step 1) Use the requests library to grab the page.
The request library that we downloaded goes and gets a response, to get a request from the webpage, we use requests.get(website URL) method. If the request is successful, it will be stored as a giant python string. We will be able to fetch the complete webpage source code when we run result.text. But the code will not be structured.

Note: This may fail if you have a firewall blocking Python/Jupyter. Sometimes you need to run this twice if it fails the first time.

Step 2) Use BeautifulSoap() method to extract data from websites. 

bs4 library already has lots of built-in tools and methods to grab information from a string of this nature (basically an HTML file). It is a Python library for pulling data out of HTML and XML files. Using BeautifulSoup() method of bs4 module we can create a soup object that contains all the ingredients of the webpage.Importing bs4 is to create a BeautifulSoup object. And we’re going to pass on two things here, result.text string and lxml as a string as a constructor argument. lxml goes through this HTML document and then figures out different CSS classes, ids, HTML elements, and tags, etc.

Extracting the data, to find the element, you need to right-click and hit inspect on the number of cases.The BeautifulSoup object has been created in our Python script and the HTML data of the website has been scraped off of the page. Next, we need to get the data that we are interested in, out of the HTML code. There is still a lot of HTML code that we do not want. Our desired data entries is wrapped in the HTML div element and inside class_= ‘maincounter-number’. We can use this knowledge to further clean up the scraped data.

Step 3) Storing the data

We need to save the scraped data in some form that can be used effectively. For this project, all the data will be saved in a Python list. We will use span to fetch data from div. We need the number of cases only, not the tags. So we will use span.string to get those numbers, and then they are stored in data[].

Now that we have the number of cases, we are ready to export our data into an Excel file.

Step 4) Processing the data

Our last step is to export the data to Ms-excel, for which we are going to use the pandas module. To load the pandas module and start working with it, import the package.  DataFrame is a 2D labeled data structure, potentially heterogeneous tabular data structure with labeled axes (rows and columns).

df = pd.DataFrame({“CoronaData”: data}) is used to create a DataFrame and give it a name and map it to the data list that we created earlier.

Next, we will give column names with df.index.Step 5) Exporting data into Excel

We are ready to export the data into Excel. We will use df.to_csv() method for this task. 
