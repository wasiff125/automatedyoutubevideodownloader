import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import WebDriverWait

# List of video links
video_links = [
    "https://www.youtube.com/watch?v=F7uKib-2f9I",
    "https://www.youtube.com/watch?v=ZIuxbHOeeA0",
    "https://www.youtube.com/watch?v=sJmWIC6U4sc",
    "https://www.youtube.com/watch?v=wKMsSTNxfHg",
]

problematic_links = []

# Initialize the Selenium WebDriver
driver = webdriver.Chrome()

# Open the website
driver.get("https://ssyoutube.com/en667NW/")

# Wait for the page to load
time.sleep(3)

# Find the input box and download button
wait = WebDriverWait(driver, 10)

# Loop through the video links
for link in video_links:
    try:
        input_box = wait.until(EC.presence_of_element_located((By.ID, "id_url")))
        download_button = wait.until(EC.presence_of_element_located((By.CLASS_NAME, "fas.fa-arrow-right")))

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

print("Downloading process completed.")
print("Problematic links:")
for link in problematic_links:
    print(link)

# Pause the script and keep the browser window open until Enter key is pressed
input("Press Enter to exit...")
