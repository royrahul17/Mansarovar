# Mansarovar Office
        ///// website open or not //////
/**
 * Checks if a website is accessible (returns HTTP status code).
 * @param {string} url The URL of the website to check.
 * @return {string} The HTTP status code or error message.
 * @customfunction
 */
 
function CHECK_WEBSITE_STATUS(url) {
  try {
    var response = UrlFetchApp.fetch(url, {muteHttpExceptions: true});
    return response.getResponseCode();
  } catch (e) {
    return 'Error: ' + e.message;
  }
}

/*****/

This will return the HTTP status code of the website. Common status codes are:
////  =CHECK_WEBSITE_STATUS() Google sheets new function 
200 for a successful response (website is open).
404 for not found (website may be down or URL is incorrect).
403 for forbidden (access is denied).
500 for internal server error (server issue).
200: The website is open and accessible.
4xx or 5xx: There is a problem with accessing the website (e.g., page not found, server error).

/*****/

        /////// Website Email Find //////

/**
 * Fetches the HTML content of a website.
 * @param {string} url The URL of the website.
 * @return {string} The HTML content of the website.
 */
 
function fetchWebsiteContent(url) {
  try {
    var response = UrlFetchApp.fetch(url);
    return response.getContentText();
  } catch (e) {
    return 'Error: ' + e.message;
  }
}

/**

 * Extracts support email addresses from HTML content.
 * @param {string} html The HTML content of the website.
 * @return {string} The support email address found in the HTML content.
   
 */

function extractSupportEmail(html) {
  var emailPattern = /[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}/g;
  var matches = html.match(emailPattern);
  return matches ? matches[0] : 'No email found';
}

/**

 * Finds the support email address for a website.
 * @param {string} websiteURL The URL of the website.
 * @return {string} The support email address found on the website.
 * @customfunction
 */
 
function findSupportEmail(websiteURL) {
  var htmlContent = fetchWebsiteContent(websiteURL);
  return extractSupportEmail(htmlContent);
}

/*******/

Google New Function =findSupportEmail()

/*******/

