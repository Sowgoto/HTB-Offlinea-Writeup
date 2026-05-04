
# Hack The Box Offlinea Challenge Write-up

## Information
Name:Sowgoto Raha Sunny  

## Challenge Information
Challenge Name: Offlinea  
Platform: Hack The Box  
Category: Web Security  

## Project Description
This project documents my individual Hack The Box challenge work for Offlinea. The goal of this challenge was to analyze the web application, identify the vulnerability chain, and retrieve the final flag.

## Environment Setup
I connected to Hack The Box using the VPN and verified the target host from the HTB challenge page. I used Kali Linux and browser-based testing tools to interact with the target application.

## Reconnaissance
I verified that the target host was alive and that the web service was running. I opened the application in Firefox and observed the Offlinea interface. I also inspected the generated PDF file and confirmed that it was a valid one-page PDF document.

## Source Code Analysis
After reviewing the provided challenge files, I identified that the application used both PHP and Python components. The public-facing PHP file communicated with an internal Flask service running on localhost. The internal service used Selenium and headless Chrome to generate PDF files.

## Vulnerability Identification
During analysis, I identified a Server-Side Request Forgery vulnerability caused by inconsistent URL parameter handling between the PHP gateway and the Flask backend. I also found a Python format-string issue that allowed access to Flask global objects, including the application SECRET_KEY.

## Exploitation Summary
The exploitation process chained multiple weaknesses. First, the SSRF bypass allowed access to the internal Flask service. Then, the format-string issue leaked the Flask SECRET_KEY. Using the leaked key, I generated a valid JWT token and accessed the protected endpoint to retrieve the secrets table and obtain the final flag.

## Result
The Offlinea challenge was successfully completed on Hack The Box.

Achievement link:  
https://labs.hackthebox.com/achievement/challenge/3164896/1108

## Files Included
- `Hack-The-Box-Offlinea-Report.pdf` — full project report
- `screenshots/` — supporting screenshots from the challenge
- `README.md` — project summary and explanation

## Conclusion
This lab demonstrated how multiple web application weaknesses can be chained together. The challenge helped me understand SSRF, insecure internal service access, Python format-string risks, Flask secret leakage, JWT token forgery, and secure application design considerations.
