# automatedyoutubevideodownloader
This Python script takes youtube video links in a list, and downloads video automatically from ssyotube website autoamtically.

This is a simple Python script that uses Selenium WebDriver to automate the process of downloading YouTube videos. It takes a list of video links and attempts to download each video in 720p resolution. If any errors occur during the download process, the script will continue to the next video link and keep track of the problematic links.

Prerequisites
Before running the script, make sure you have the following:

Python 3.x installed on your system.
The selenium package installed. You can install it using pip:
Copy code
pip install selenium
The appropriate WebDriver for your browser installed and configured. This script uses the Chrome WebDriver by default. You can download it from the official Selenium website: https://www.selenium.dev/documentation/en/webdriver/driver_requirements/
Usage
Clone this repository or download the script file.
Open the script in a text editor of your choice.
Modify the video_links list to include the YouTube video links you want to download.
Save the changes.
Open a terminal or command prompt and navigate to the directory containing the script.
Run the script using the following command:
Copy code
python script_name.py
Script Explanation
Import necessary libraries:

javascript
Copy code
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import WebDriverWait
Define the list of video links and an empty list to store problematic links:

css
Copy code
video_links = [    "https://www.youtube.com/watch?v=F7uKib-2f9I",    "https://www.youtube.com/watch?v=ZIuxbHOeeA0",    "https://www.youtube.com/watch?v=sJmWIC6U4sc",    "https://www.youtube.com/watch?v=wKMsSTNxfHg",]

problematic_links = []
Initialize the Selenium WebDriver (Chrome in this case):

makefile
Copy code
driver = webdriver.Chrome()
Open the website for video download:

csharp
Copy code
driver.get("https://ssyoutube.com/en667NW/")
Wait for the page to load:

css
Copy code
time.sleep(3)
Find the input box and download button using the WebDriverWait object:

scss
Copy code
wait = WebDriverWait(driver, 10)
input_box = wait.until(EC.presence_of_element_located((By.ID, "id_url")))
download_button = wait.until(EC.presence_of_element_located((By.CLASS_NAME, "fas.fa-arrow-right")))
Loop through the video links and attempt to download each video:

python
Copy code
for link in video_links:
    try:
        # Enter the link in the input box
        input_box.clear()
        input_box.send_keys(link)
        input_box.send_keys(Keys.RETURN)

        # Wait for the search to complete and the popup to appear
        time.sleep(5)

        # Find the 720p download button in the popup
        download_720_button = wait.until(EC.presence_of_element_located((By.ID, "download-mp4-720-audio")))

        # Click the 720p download button
        download_720_button.click()

        # Wait for the download to start
        time.sleep(2)

        print(f"Download started for link: {link}")
    except Exception as e:
        print(f"An error occurred for link: {link}")
        print(f"Error details: {str(e)}")
        problematic_links.append(link)
        continue
Print the completion message and display any problematic links:

bash
Copy code
print("Downloading process completed.")
print("Problematic links:")
for link in problematic_links:
    print(link)
Pause the script and keep the browser window open until the Enter key is pressed:

css
Copy code
input("Press Enter to exit...")
Note
This script uses the ssyoutube.com website for video download. Please make sure to comply with the terms and conditions of the website and respect the rights of content creators.
The script is provided as-is and may require adjustments depending on changes to the target website or Selenium framework.
Use this script responsibly and for personal use only. Respect the intellectual property rights of content creators and do not distribute or misuse downloaded videos.
