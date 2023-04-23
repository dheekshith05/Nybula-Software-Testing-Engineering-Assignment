# Nybula-Software-Testing-Engineering-Assignment
Test Planning for Nbyula Marketplace Website:

Introduction:
Nbyula is a new marketplace website that is currently in development. The project is in the initial stages, and testing has not been conducted yet. The purpose of this mini-test plan is to define the test activities for the next six months until the delivery of the project. The test plan is designed to ensure that the website is functional, user-friendly, and meets all the requirements of the stakeholders.

Test Activities:
The following test activities will be performed over the next six months:

1. Requirements Review: Review and analyze the requirements documents provided by the stakeholders. Identify any ambiguities or missing information that may affect the testing process.

2. Test Planning: Develop a comprehensive test plan that includes the test objectives, scope, test strategies, test scenarios, and test cases. Define the testing environment and test data requirements.

3. Test Execution: Execute the test cases and scenarios as per the test plan. Identify defects and report them to the development team. Retest the defects once they have been fixed.

4. Test Reporting: Prepare test reports that include the test results, defect status, and overall project status. Share the reports with the stakeholders and the development team.

5. Test Automation: Develop test automation scripts for regression testing. Implement test automation tools and frameworks to speed up the testing process.

6. Performance Testing: Perform load and stress testing to ensure that the website can handle a large number of users simultaneously. Identify any bottlenecks in the system and report them to the development team.

Timeline:
The following timeline is proposed for the test activities:

Month 1: Requirements Review and Test Planning
Month 2-3: Test Execution
Month 4: Test Reporting and Test Automation
Month 5: Performance Testing
Month 6: Final Testing and Bug Fixes

Conclusion:
This mini-test plan outlines the test activities that will be conducted for the Nbyula marketplace website for the next six months until delivery. The test plan will ensure that the website is functional, user-friendly, and meets all the requirements of the stakeholders. The proposed timeline will help in timely delivery of the project with high-quality standards.

Part 2 Testing

For this task, I have decided to use the Selenium WebDriver with Python and Pytest as the test framework. I will be automating the following scenarios:

Access https://nbl.one/feed, validate if there is at least 1 quest.
Access https://nby.la/rdJuXp and try booking the skylift
Access https://nbl.one/listings, then scrape all the cards for title, price and link associated with each card.
Prerequisites:

Python installed
Selenium WebDriver installed
Pytest installed
Setup:

Clone the project from the repository using git clone https://github.com/<your-username>/nbl-test-automation.git
Navigate to the project directory using cd nbl-test-automation
Install the dependencies using pip install -r requirements.txt
Download the appropriate version of the WebDriver for your browser and operating system and add it to the project directory.
Run the tests using pytest -v
Test Implementation:

1.Access https://nbl.one/feed, validate if there is at least 1 quest.
python

def test_quest_present():
    driver.get("https://nbl.one/feed")
    quests = driver.find_elements_by_css_selector("div.feed-card")
    assert len(quests) >= 1
2.Access https://nby.la/rdJuXp and try booking the skylift
python

def test_booking_skylift():
    driver.get("https://nby.la/rdJuXp")
    booking_button = driver.find_element_by_css_selector("a[data-gtm-event='Click - Book now']")
    booking_button.click()
    driver.switch_to.window(driver.window_handles[-1])
    book_now_button = driver.find_element_by_css_selector("button[data-gtm-event='Click - Book Now']")
    book_now_button.click()
    assert "Confirm Your Booking" in driver.title
3.Access https://nbl.one/listings, then scrape all the cards for title, price and link associated with each card.
python

def test_scrape_listings():
    driver.get("https://nbl.one/listings")
    listings = driver.find_elements_by_css_selector("div.listing-card")
    for listing in listings:
        title = listing.find_element_by_css_selector("h3.title").text
        price = listing.find_element_by_css_selector("div.price").text
        link = listing.find_element_by_css_selector("a.card-link").get_attribute("href")
        print(f"Title: {title}, Price: {price}, Link: {link}")
Report Generation:
To generate a report, I have used the Pytest HTML plugin. The plugin generates an HTML report of the test execution with details on the test results and test coverage.

Pipeline Setup:
I have created a basic pipeline using GitHub Actions to automatically run the tests on every commit to the repository. The pipeline is defined in the .github/workflows/main.yml file and is triggered on a push event.
