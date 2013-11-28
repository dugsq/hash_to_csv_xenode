hash-to-csv-xenode
==================

**Hash-to-CSV Xenode** parses through hashes that it receives in its input message data and converts the data into CSV format. Each incoming message with data should be an array with a hash inside for each row. If there was no readable data from the message, the Xenode discards the message. The Configuration File must contain the default row and column delimiters. Set 'has_header' to true in the Configuration File if you need to generate a header containing the column names on the first line.

###Configuration File Options:###
* loop_delay: defines number of seconds the Xenode waits before running the Xenode process. Expects a float. 
* enabled: determines if the Xenode process is allowed to run. Expects true/false.
* debug: enables extra debug messages in the log file. Expects true/false.
* has_header: determines whether to generate a header row for the CSV containing the column names. Expects true/false.
* row_delim: specifies the row delimiter for parsing of the CSV file. Expects a string.
* col_delim: specifies the column delimiter for parsing of the CSV file. Expects a string.

###Example Configuration File:###
* enabled: false
* loop_delay: 30
* debug: false
* has_header: true
* row_delim: "\n"
* col_delim: ","

###Example Input:###
* msg.data:  [{"From_User"=>"cmscrawler", "Tweet_Content"=>"http://t.co/8RxECaPlvD: Change from WordPress to Drupal. The site is hosted in The United States http://t.co/8RxECaPlvD #cms"}]

###Example Output:###
* msg.data: "From_User,Tweet_Content\ncmscrawler,http://t.co/8RxECaPlvD: Change from WordPress to Drupal. The site is hosted in The United States http://t.co/8RxECaPlvD #cms"
