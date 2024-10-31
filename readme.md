# DataforthaiWebscrapperV2

This project is a web scraper program for a specific website called DataForThai (www.dataforthai.com). It is primarily written in JavaScript to make requests to the site, perform pre-indexing, and provide utility tools for this project. We also use Pandas in Python for further analysis and table editing.

## Collaborators and Scopes

- **OteEnded**: Responsible for scraping data within the catagory ID range [46101, 100000].
- **BJesaya**: Responsible for scraping data within the catagory ID range [0, 46100].

## Requirements

- **Node.js**: Version 18 or higher. [Download Node.js](https://nodejs.org/en/download/)
- **Python**: Version 3.9 or higher. [Download Python](https://www.python.org/downloads/)

## How to Use This Project

Follow these steps to run this project:

1. **Clone the repository**:
    ```sh
    git clone <repository_url>
    ```
2. **Install Node.js** (version 18 or higher). You can download it from [here](https://nodejs.org/en/download/).
3. **Navigate to the root of the project** using the terminal:
    ```sh
    cd <path_to_project>
    ```
4. **Install the necessary packages**:
    ```sh
    npm install
    ```
5. **Acquire a login token (PHPSESSID)** from [DataForThai](https://www.dataforthai.com/):
    1. Go to [DataForThai](https://www.dataforthai.com/).
    2. Register and log in to your account.
    3. Open the Inspect menu from your browser (usually by right-clicking and selecting "Inspect" or pressing `F12`).
    4. Navigate to the "Application" tab.
    5. Select "Cookies" and find `www.dataforthai.com`.
    6. Find the cookie with the key `PHPSESSID` and copy the value.
6. **Rename the `.env-example.json` file to `.env.json`** and replace the `value` key in the `cookie` object with your token.
7. **Move the company ID list by category** that you want to scrape from `./DataForThaiCompanyIdsByCategories` to `./Assigned`.
8. **Run `main.js`** or type in the terminal:
    ```sh
    npm start
    ```
    or for Windows run the `start.bat`
9. **Wait until the process is done**. The results will be in the `./Target` directory as JSON files.
10. **Import/convert the JSON files** to your desired format. You can convert them to a DataFrame in pandas to process the data further.

## npm Scripts

The project includes several npm scripts to help manage and run different parts of the project:

- **`npm start`**: This is the classic start script. It calls the `main.js` script to start the web scraping process.
- **`npm run report`** or **`npm run count`**: This script reads the target, the result, or anything that can calculate the progress and reports how much progress the project has made.
- **`npm run tocsv`**: This script starts the Python subproject part, which handles data filtering, cleaning, and converting JSON results to CSV. The script manages the Python virtual environment cross-platform (not fully tested on Mac/Linux).
- **`npm run cookiesetter`** or **`npm run cookie <PHPSESSID>`**: This script quickly sets the cookie for the session.

## Project Directory Structure

- **Assigned**: Directory to put company IDs grouped by category CSV files from `DataForThaiCompanyIdsByCategories`. The main script will read from this directory and work on scraping according to the company ID list in this directory.
- **DataForThaiCompanyIdsByCategories**: Directory containing a list of all company IDs grouped by category from the whole DataForThai.
- **BusinessCatagoryList.csv**: File that works like a dictionary for categories to resolve metadata such as category name and amount of companies.
- **Logs**: Directory to hold log files for later reading and debugging.
- **Target**: Directory to hold data from scraping, grouped by category (according to `Assigned` directory) in the form of JSON (list of records).
- **Result**: Directory to hold results from converting JSON (in `Target` directory) to Excel-loadable CSV.
- **Python**: Directory to hold Python code that functions as a JSON to CSV converter. Since it works with pandas, it also includes some cleaning processes.
- **Temp**: Directory to hold the last HTML page that was scraped to provide more clues in case of errors.
- **.env.json**: Environment/config file that contains the cookie (as described in the "How to Use This Project" section), delay range (min and max seconds that the program will randomly delay to make it harder to tag as a bot), and `previewpage` (if set to true, the browser window with the current scraping page will pop up during scraping for debugging purposes).
- **.env-example.json**: Example environment/config file that is included in the repository so others can rename it to `.env.json` to use as their environment/config.
- **start.bat**: Batch file to easily run the scraping process (for Windows).
- **main.js**: Main scraping process script.

## Dev Contact

If you have any questions, feel free to contact OteEnded:
- **Email**: ratnaritjumomg@gmail.com
- **Discord**: oteended
- **Line**: (if already have contact)