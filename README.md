# MPhishing-Website-Detection-Google-Chrome-Extension-with-Machine-Learning-Model

## Objective
The objective is to develop a Google Chrome extension that utilizes HTML, CSS, JavaScript, and a trained machine learning model to detect malicious URLs. The extension will intercept URL loading in the web browser and perform a check using the trained model to determine if the URL is safe or unsafe. The extension will provide real-time feedback to the user by displaying pop-up messages. If the URL is deemed safe, the loading process will continue, and a pop-up message will confirm the safety. If the URL is considered unsafe, the loading process will be halted, and a pop-up message will inform the user about the potential danger. The extension will seek user permission to continue loading the unsafe URL or stop loading altogether. By achieving this objective, the Chrome extension will enhance user security by proactively identifying and notifying users about potentially malicious URLs.

## Data Collection
For the purpose of this project, a dataset containing URLs classified as legitimate (0) and phishing (1) was required. A suitable dataset was discovered on Kaggle, which had been specifically curated for webpage classification as malicious or benign. This dataset included extracted attributes from websites, which could be utilized for classification purposes. Additionally, the dataset encompassed raw page content, including JavaScript code, which could be employed as unstructured data in Deep Learning or further attribute extraction. The data was obtained through web crawling using MalCrawler, and the labels were verified using the Google Safe Browsing API. 

source: https://www.kaggle.com/datasets/aksingh2411/dataset-of-malicious-and-benign-webpages

To tailor the dataset to my specific needs, I modified it by retaining only the "url" feature and the corresponding "label". Furthermore, to maintain balance in the dataset, I selected 8000 instances from each label type and created separate data files for analysis and modeling.

I create two data files as follows.
- “phishing.csv” – contain 8000 phishing URLs.
- “legitimate.csv” – contain 8000 legitimate URLs.

## Feature Extraction
The next step involved the extraction of features from the URLs dataset. These extracted features were categorized into three main groups: 
1.	**Address Bar based Features**,
2.	**Domain based Features**, and 
3.	**HTML & Javascript based Features**.

**1. Address Bar based Features**
the following ones were specifically chosen:
- Domain of URL: This feature captures the domain of the URL, providing insights into the website's origin.
- IP Address in URL: This feature detects the presence of an IP address within the URL, which can be indicative of malicious activity.
- "@" Symbol in URL: The presence of the "@" symbol in a URL can indicate potential email-related attacks or credential harvesting attempts.
- Length of URL: This feature measures the length of the URL, as longer URLs are often associated with phishing attempts.
- Depth of URL: The depth of a URL represents the number of subdirectories or levels in the URL structure. A deeper URL structure can sometimes be an indication of phishing.
- Redirection "//" in URL: This feature detects the occurrence of double slashes ("//") in the URL, which can be a sign of suspicious redirections.
- "http/https" in Domain name: This feature identifies whether the domain name contains "http" or "https," as the presence of "http" might indicate a less secure connection.
- Using URL Shortening Services: This feature determines whether the URL utilizes a URL shortening service which can be used to obfuscate malicious links.
- Prefix or Suffix "-" in Domain: This feature identifies the presence of a prefix or suffix "-" in the domain name, as it can be indicative of suspicious activity or attempts to mimic legitimate websites.
By considering these specific address bar-based features, we aim to capture key characteristics that can aid in the identification and classification of phishing URLs.

**2.	Domain based Features**
In addition to Address Bar based Features, another category of features extracted from the URLs dataset pertains to Domain based Features. Numerous features can be derived from this category, but for this project, the following features were specifically considered:
- DNS Record: This feature provides information about the DNS (Domain Name System) record associated with the domain. It helps in analyzing the legitimacy of the domain and identifying any potential anomalies.
- Website Traffic: This feature captures data related to the traffic received by the website. It offers insights into the popularity and reputation of the domain, allowing for the identification of suspicious or low-traffic domains.
- Age of Domain: The age of a domain indicates the duration since its creation. This feature is useful in determining if a domain is relatively new or has been in existence for an extended period. Phishing websites are often short-lived, so analyzing the age of a domain can be beneficial for classification purposes.
- End Period of Domain: This feature signifies the expiration date of the domain. It helps in assessing whether a domain is about to expire or has already expired, which can be indicative of malicious activity or abandonment.

By considering these domain-based features, we aim to incorporate additional characteristics that can contribute to the accurate classification of URLs as legitimate or phishing.

**3.	HTML & Javascript based Features**
The third category of features extracted from the URLs dataset pertains to HTML and JavaScript based Features. Within this category, several features can be derived, and for this project, the following features were specifically considered:
- IFrame Redirection: This feature detects the presence of an IFrame tag in the webpage's HTML code, which can be used for malicious purposes such as redirecting the user to an unintended website or embedding malicious content.
- Status Bar Customization: The customization of the browser's status bar is often employed by phishing websites to deceive users. This feature captures any attempts to modify the status bar, enabling the identification of potential phishing URLs.
- Disabling Right Click: Phishing websites may attempt to disable the right-click functionality in order to prevent users from accessing browser features such as viewing source code or opening links in new tabs/windows. This feature detects any such attempts at disabling right-click functionality.
- Website Forwarding: This feature identifies instances where the webpage implements automatic website forwarding. Phishing websites may use this technique to redirect users to malicious websites without their knowledge or consent.

By incorporating these HTML and JavaScript based features, we aim to capture specific indicators within the webpage's code that can aid in the accurate identification and classification of phishing URLs.


