# React Native - Coding Challenge

Building a simple react-native application with 2 views that lets the user load a list of articles from the fake API.
By default we will be requesting the first page of articles and if the user scrolls down the article user pages must be requested and added to the existing articles.
API specification (GET ALL Articles: https://demo.wp-api.org/wp-json/wp/v2/posts?per_page=1) paginating 10 elements on each page until no results are returned (last page) or until we reached the last page using the http response header "X-WP-TotalPages"

Pagination attributes:
per_page (specifies the number of items per page, and goes in query params)
offset (specified the number of items to skip, the current index, must be also in query params)

To determine how many pages of data are available, the API returns two header fields with every paginated response:
X-WP-Total: the total number of records in the collection
X-WP-TotalPages: the total number of pages encompassing all available records
https://developer.wordpress.org/rest-api/using-the-rest-api/pagination/


## REQUIREMENTS
You can build the layout as you prefer but at least having a shared header between the views, a place to configure the main design attributes (colors, fonts, etc).
The application will contain 2 simple views, a intro page with the amount of articles fetched till that moment, and a button to navigate to the next view where all the articles are listed.

### MainView 
On the first view (main), we will display the amount of articles stored in the reducer and a button to go to the list view (Stack navigation).
At the begining 0 articles and a button to go to the next page, but also the user can go back to the first screen after having fetched 
more articles and see how the total amount has changed.

### ListView 
The second view contains the list of the articles that have been fetched till that moment. 
The user can interact with the view in 2 ways:
1. If no articles are found when entering the request, the first page of articles gets loaded (dispatch the fetchArticles action on first page)
2. When the user scrolls down in the application, we must load the next page of articles based on the last page stored. 
If the query returns >= 10 results, or if we still have pages available "X-WP-TotalPages" header, we must save the current page in the reducer and request the next-one.

## BONUS POINTS:
1. Paginating articles.
2. Stack navigator (display the header + backbutton when navigating between the 2 views).
3. A couple of test snapshots to test that everything is rendering correctly and nothing has changed.
4. Making the UI colors, fonts and other settings configurable from a constants.js file so we can switch colors and fonts easily.
5. Persistent storage (Async storage)

If during the process you need help or explanation please contact: javierr@draagu.com