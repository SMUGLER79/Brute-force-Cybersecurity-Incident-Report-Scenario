# Brute Force Cybersecurity-Incident Report-Scenario

# Introduction

This report documents a cybersecurity incident involving a brute force attack on the web server of yummyrecipesforme.com, a website specializing in recipes and cookbooks. A former employee exploited weak security controls to repeatedly guess the default admin password, gaining unauthorized access to the admin panel. After compromising the website, the hacker embedded malicious JavaScript into the source code, prompting visitors to download a file containing malware. This malware redirected users to a fake website, greatrecipesforme.com, which further propagated the attack. Multiple network protocols, including DNS, HTTP, and TCP, facilitated the attack’s execution. This report details the step-by-step analysis of the incident, outlines the network communication involved, and provides recommendations to prevent similar attacks, including implementing measures to secure administrative credentials and mitigate brute force attacks.

# Scenario

You are a cybersecurity analyst for yummyrecipesforme.com, a website that sells recipes and cookbooks. A former employee has decided to lure users to a fake website with malware. 

The former employee/ hacker executed a brute force attack to gain access to the web host. They repeatedly entered several known default passwords for the administrative account until they correctly guessed the right one. After they obtained the login credentials, they were able to access the admin panel and change the website’s source code. They embedded a javascript function in the source code that prompted visitors to download and run a file upon visiting the website. After embedding the malware, the hacker changed the password to the administrative account. When customers download the file, they are redirected to a fake version of the website that contains the malware. 

Several hours after the attack, multiple customers emailed yummyrecipesforme’s helpdesk. They complained that the company’s website had prompted them to download a file to access free recipes. The customers claimed that, after running the file, the address of the website changed and their personal computers began running more slowly. 

In response to this incident, the website owner tries to log in to the admin panel but is unable to, so they reach out to the website hosting provider. You and other cybersecurity analysts are tasked with investigating this security event.

To address the incident, you create a sandbox environment to observe the suspicious website behavior. You run the network protocol analyzer tcpdump, then type in the URL for the website, yummyrecipesforme.com. As soon as the website loads, you are prompted to download an executable file to update your browser. You accept the download and allow the file to run. You then observe that your browser redirects you to a different URL, greatrecipesforme.com, which contains the malware.  

The logs show the following process:
  - The browser initiates a DNS request: It requests the IP address of the yummyrecipesforme.com URL from the DNS server.
  - The DNS replies with the correct IP address. 
  - The browser initiates an HTTP request: It requests the yummyrecipesforme.com webpage using the IP address sent by the DNS server.
  - The browser initiates the download of the malware.
  - The browser initiates a DNS request for greatrecipesforme.com.
  - The DNS server responds with the IP address for greatrecipesforme.com.
  - The browser initiates an HTTP request to the IP address for greatrecipesforme.com.

A senior analyst confirms that the website was compromised. The analyst checks the source code for the website. They notice that javascript code had been added to prompt website visitors to download an executable file. Analysis of the downloaded file found a script that redirects the visitors’ browsers from yummyrecipesforme.com to greatrecipesforme.com. 

The cybersecurity team reports that the web server was impacted by a brute force attack. The disgruntled hacker was able to guess the password easily because the admin password was still set to the default password. Additionally, there were no controls in place to prevent a brute force attack. 

Your job is to document the incident in detail, including identifying the network protocols used to establish the connection between the user and the website.  You should also recommend a security action to take to prevent brute force attacks in the future.

# Work Flow

1. Analyse the [tcpdump traffic logs](https://github.com/SMUGLER79/Brute-force-Cybersecurity-Incident-Report-Scenario/blob/main/tcpdump%20traffic%20log.pdf)
2. Identify the network protocol involved in the incident
3. [Document the incident](https://github.com/SMUGLER79/Brute-force-Cybersecurity-Incident-Report-Scenario/blob/main/Brute%20Force%20Security%20incident%20report.pdf)

# Conclusion

In conclusion, the cybersecurity incident at yummyrecipesforme.com highlights the critical need for robust security measures to prevent brute force attacks and unauthorized access. The incident exploited weak administrative password controls, allowing the attacker to embed malicious code and redirect users to a fake, malware-infected website. Network protocols such as DNS, TCP, HTTP, and IP played a central role in facilitating the attack and subsequent malicious activity. To mitigate future risks, implementing strong password policies, enforcing two-factor authentication, monitoring login attempts, and limiting failed login attempts are essential steps. These measures, combined with regular security audits, will significantly enhance the website’s defense against similar threats.
