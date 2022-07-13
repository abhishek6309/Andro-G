<h2>AndroGoat</h2> AndroGoat is purposely developed open source vulnerable/insecure app using Kotlin. Security Testers/Professionals/Enthusiasts, Developers...etc. can use this application to understand and defend the vulnerabilities in Android platform. This is the first vulnerable app developed using Kotlin.If you are looking to learn Android Application Security Testing then AndroGoat is a perfect solution. 

I strongly believe this AndroGoat will help many people to learn Android Application Security Testing.

***Happy learning***

Vulnerabilities covered in this app:

1. Root Detection</br>
2. Emulator Detection</br>
3. Insecure Data Storage – Shared Prefs - 1</br>
4. Insecure Data Storage - Shared Prefs - 2</br>
5. Insecure Data Storage - SQLite</br>
6. Insecure Data Storage – Temp Files</br>
7. Insecure Data Storage – SD Card</br>
8. Keyboard Cache</br>
9. Insecure Logging</br>
10. Input Validations – XSS</br>
11. Input Validations – SQLi</br>
12. Input Validations – WebView</br>
13. Unprotected Android Components – Activity</br>
14. Unprotected Android Components –Service</br>
15. Unprotected Android Components – Broadcast Receivers</br>
16. Unprotected Android Components – Content Providers (Coming Soon)</br>
17. Hard coding issues</br>
18. Network intercepting – HTTP</br>
19. Network intercepting – HTTPS</br>
20. Network intercepting – Certificate Pinning</br>
21. Misconfigured Network_Security_Config.xml</br>
22. Android Debuggable</br>
23. Android allowBackup</br>
24. Custom URL Scheme</br>
25. Broken Cryptography </br>
26. QR Code Scanning (Coming Soon)</br>
27. Fingerprint Authentication (Coming Soon)</br>
</br>

Download apk file from https://github.com/satishpatnayak/MyTest/blob/master/AndroGoat.apk , install and ride AndroGoat..</br></br>

Feedbank and Ideas are welcome. Please reach me satishkumarpatnayak@live.com </br>
Follow me on Twiiter for update on blogs, changes...etc https://twitter.com/satish_patnayak

 # Performing Static ApplicationSecurity Testing Using SonarQube on AndroGoat:

Download DVWA source code from https://github.com/satishpatnayak/AndroGoat

Open SonarQube Click on create project and add an project name like " AndroGoa Source code review "

Go to With the configuration best suited for you in this we will go manually with GitHub Actions

we have to Create GitHub Secrets in our repository containing Vulnerable web application source code

Create a " sonar-project.properties " file in your repository and paste the content mentioned in below :
sonar.projectKey=Andro-Goat-Source-code-review

Create or update your .github/workflows/build.ymland paste the content mentioned :

 name: Build on:
 push:
   branches:
     - master # or the name of your main branch
jobs
 build:
   name: Build
   runs-on: ubuntu-latest
   steps:
     - uses: actions/checkout@v2
       with:
         fetch-depth: 0
     - uses: sonarsource/sonarqube-scan-action@master
       env:
         SONAR_TOKEN: $Template:Secrets.SONAR TOKEN
         SONAR_HOST_URL: $Template:Secrets.SONAR HOST URL
     # If you wish to fail your job when the Quality Gate is red, uncomment the
     # following lines. This would typically be used to fail a deployment.
     # - uses: sonarsource/sonarqube-quality-gate-action@master
     #   timeout-minutes: 5
     #   env:
     #     SONAR_TOKEN: $Template:Secrets.SONAR TOKEN

Commit and push your code to start the analysis. Each new push you make on your main branch will trigger a new analysis in SonarQube

# Observations:

SonarQube will give you detailed analysis report within 5 minutes which will help you to improve your code quality

The results of analysis will be as following:

- 1 Bugs
- 2 Vulnerabilities
- 52 Code Smells
- 0.0 % Duplications
You can then see the details of bugs , vulnerabilities, code smells , etc. found by clicking on then

it will also shows suggestion about how you can improve your code and mitigate the bugs

ex:

  android:name=".InsecureStorageTempActivity"
44				
            android:label="@string/tempFile" />
45				
        <activity
46				
            android:name=".AccessControlIssue1Activity"
47				
            android:label="@string/activity" />
48				
        <activity
Implement permissions on this exported component.

49				
            android:name=".AccessControl1ViewActivity"
50				
            android:label="@string/activity">
51				
            <intent-filter>
52				
                <action android:name="android.intent.action.VIEW" />
53				
                <category android:name="android.intent.category.DEFAULT" />
54				
                
57				
            </intent-filter>

