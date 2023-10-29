![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image4.png){width="2.3381944444444445in"
height="2.3381944444444445in"}

**Requirements Specification Document**

> ***FUNiX Passport***

**Revision History**

  -----------------------------------------------------------------------------
  **Date**          **Version**   **Description**             **Author**
  ----------------- ------------- --------------------------- -----------------
  18/10/2023        v1.0          Funix Passport              Hoang Minh Nguyen

                                                              

                                                              

                                                              
  -----------------------------------------------------------------------------

**Table of Contents**

**Project overview 4**

> Project summary 4
>
> Project scope 4

**Project Requirements and Specifications 4**

> Functional Requirements 4
>
> Non-functional requirements 4
>
> System Security 5
>
> Availability and responsiveness 5
>
> Efficiency 5
>
> Software Specifications 5

**Software architecture and design 5**

> Software architecture 5
>
> [Usecase](#usecase) 6
>
> Usecase of User 7
>
> Usecase of Translator 8
>
> Usecase of Reviewer 8
>
> Usecase of Administrator 8
>
> Usecase of the System 8
>
> [Class Diagram](#class-diagram) 9
>
> [Sequence Diagram](#_s5lpyvciae7u) 10
>
> [Activity Diagram](#activity-diagram) 10

**Specification document**

1.  # **Project overview**

    1.  ## **Project summary**

-   System: Funix Passport

-   The objective of the FUNiX Passport project is to develop a system
    > that facilitates students\' access to Vietnamese documents,
    > including video subtitles and document pages. The system aims to
    > enhance students\' comprehension of educational materials without
    > relying solely on existing English auto-subtitles.

    1.  ## **Project scope**

```{=html}
<!-- -->
```
-   The project will provide user-friendly subtitles for course learning
    > materials, translated by academic professionals from Funix.

-   The system serves a heterogeneous user base consisting of learners
    > engaged in Funix\'s online courses, translators contributing to
    > the translation process, administrators overseeing system
    > management, and subtitle reviewers responsible for ensuring
    > quality and accuracy of subtitles.

-   The system will be deployed as a Google Chrome browser extension.

2.  # **Project Requirements and Specifications**

    1.  ## **Functional Requirements**

```{=html}
<!-- -->
```
a)  Backend:

-   Facilitate the seamless submission of corresponding subtitle files
    > by translators for each video hosted on MOOC sites, as well as the
    > upload of translated documents. This functionality empowers both
    > translators and administrators to efficiently oversee and maintain
    > translation and subtitle-related data.

-   A comprehensive database encompasses a curated collection of
    > subjects, video links, and accompanying visit metrics for each
    > video.

```{=html}
<!-- -->
```
-   Translator:

```{=html}
<!-- -->
```
-   Upload the translated Vietnamese subtitle file:

```{=html}
<!-- -->
```
-   Access the upload screen and provide necessary information such as
    > Video Name, Video URL, Course ID, and Video ID.

-   Attach the translated subtitle file.

-   Upon clicking submit, the application will facilitate the upload and
    > storage of data in the database.

```{=html}
<!-- -->
```
-   Upload translated Document file in Vietnamese:

```{=html}
<!-- -->
```
-   Input the Translation Name and URL of the Document.

-   Attach the translated Document file.

```{=html}
<!-- -->
```
-   View the list of uploaded translation files:

```{=html}
<!-- -->
```
-   Two Dashboards will be available, one displaying subtitle
    > translations and the other displaying Document translations.

```{=html}
<!-- -->
```
-   Download the translated file:

```{=html}
<!-- -->
```
-   By clicking on the link provided on the Dashboard, users can
    > download the translation data, including the Subtitle file or
    > Document file.

```{=html}
<!-- -->
```
-   Download the translated file:

```{=html}
<!-- -->
```
-   By clicking on the link provided on the Dashboard, users can
    > download the translation data, including the Subtitle file or
    > Document file.

```{=html}
<!-- -->
```
-   Search for translations using filters:

```{=html}
<!-- -->
```
-   Have the ability to search for translations using different filters
    > such as Translation name, URL, Translator, Course ID, and Video
    > ID.

```{=html}
<!-- -->
```
-   Delete subtitle files or documents:

```{=html}
<!-- -->
```
-   Can choose to delete that particular translation.

```{=html}
<!-- -->
```
-   Edit information:

```{=html}
<!-- -->
```
-   Can opt to make edits to the information associated with that
    > translation.

-   Two types of editing are available: Edit the metadata of the
    > translation file or Re-upload a different translation file in
    > place of the original.

```{=html}
<!-- -->
```
-   Administrator:

```{=html}
<!-- -->
```
-   Primarily responsible for user account management.

```{=html}
<!-- -->
```
-   Deletion of user accounts.

-   Granting permissions to a user (transferring the role from User to
    > Translator).

-   Revoking permissions from a user (reverting the role from Translator
    > to User).

```{=html}
<!-- -->
```
-   Reviewer

```{=html}
<!-- -->
```
-   View the list of uploaded translation files:

```{=html}
<!-- -->
```
-   Two Dashboards will be available, one displaying subtitle
    > translations and the other displaying Document translations.

```{=html}
<!-- -->
```
-   Search for translations using filters:

```{=html}
<!-- -->
```
-   Have the ability to search for translations using different filters
    > such as Translation name, URL, Translator, Course ID, and Video
    > ID.

```{=html}
<!-- -->
```
-   Entrusted with the responsibility of meticulously assessing the
    > precision of the Translator\'s video translations and providing
    > constructive feedback.

-   Download the translated file:

```{=html}
<!-- -->
```
-   By clicking on the link provided on the Dashboard, users can
    > download the translation data, including the Subtitle file or
    > Document file.

b)  Extension

-   Establishing communication with the Backend system, enabling the
    > retrieval of translation data and facilitating the display of said
    > translated content for students\' utilization.

-   Extract the URL, enabling the retrieval of pertinent information
    > such as video_ID or course_ID.

-   Initiate a request to the Backend, enclosing the extracted data:

```{=html}
<!-- -->
```
-   If the website originates from MOOC sources, the Extension will
    > submit the course_ID and video_ID to procure the corresponding
    > subtitles.

-   In all other cases, the Extension will seek to locate and translate
    > the Document by transmitting the entire URL to the Backend. .

```{=html}
<!-- -->
```
-   Once the Extension receives the returned data from the Backend, it
    > will display a popup to prompt the user to decide whether they
    > wish to utilize the translation or not. If the user consents to
    > the translation, the translated content will be presented to the
    > user.

    1.  ## **Non-functional requirements**

a)  Backend

-   Execute database operations to facilitate the management of
    > translation files.

-   Incorporate a dedicated Database designed to store comprehensive
    > Metadata for each translation, encompassing both the data
    > contributed by the Translator and the data generated internally by
    > itself.

-   Regarding the translation of Videos, the Database will store the
    > subsequent data:

```{=html}
<!-- -->
```
-   ID (auto-generated): The unique identifier for the translation.

-   Translator (auto-generated): The name of the translator who uploaded
    > the translation.

-   UploadedDate (auto-generated): The timestamp indicating when the
    > translation was uploaded.

-   Name: The designated name for the translation.

-   URL: The web address associated with the translation, which can
    > refer to a document website or a video link.

-   Video ID: The specific identification number assigned to the
    > corresponding video.

-   Course ID: The identifier for the video source in the Vietnamese
    > language.

-   Vietnamese Subtitle URL: The file path leading to the translated
    > Vietnamese subtitle file.

-   English Subtitle URL (Optional): The file path leading to the
    > translated English subtitle file, if avail

```{=html}
<!-- -->
```
-   For Document translations, the database will include the following
    > fields:

```{=html}
<!-- -->
```
-   ID (auto-generated): The unique identifier for the translation.

-   Translator (auto-generated): The name of the translator who uploaded
    > the translation.

-   UploadedDate (auto-generated): The timestamp indicating when the
    > translation was uploaded.

-   Name: The designated name for the translation.

-   URL: The web address associated with the translation, which can
    > refer to a document website or a video link.

-   Document URL: The file path leading to the translated Document file.

    1.  ### ***System Security***

```{=html}
<!-- -->
```
-   Stringent security measures are imperative to ensure the robust
    > protection of data, which is securely stored within a fortified
    > Database.

-   The implementation requires the utilization of API Keys or Tokens to
    > accurately authenticate and authorize access to, as well as
    > modification of, data residing within the Database.

    1.  ### ***Availability and responsiveness***

```{=html}
<!-- -->
```
-   The system\'s user interface is intentionally designed with a
    > user-friendly approach, ensuring accessibility and ease of
    > comprehension for individuals with varying levels of technological
    > proficiency.

-   The development focus of the Extension primarily revolves around its
    > integration within the Google Chrome browser environment,
    > strategically devised to meet users\' demand seamlessly and
    > promptly whenever necessitated.

    1.  ### ***Efficiency***

```{=html}
<!-- -->
```
-   The system is expected to exhibit consistent and reliable
    > performance, ensuring promptness in displaying translations upon
    > student access to the website, with an upper limit of 1 second.

-   The processing speed for submitting and executing Translator
    > operations should be swift, with an average response time for each
    > operation not exceeding 0.5 seconds.

    1.  ## **Software Specifications**

```{=html}
<!-- -->
```
-   Document Access:

```{=html}
<!-- -->
```
-   The system should support different file formats such as PDF, DOC,
    > PPT, and video subtitles in SRT format.

-   The system\'s user interface is intentionally designed with a
    > user-friendly approach, ensuring accessibility and ease of
    > comprehension for individuals with varying levels of technological
    > proficiency.

```{=html}
<!-- -->
```
-   Document Translation:

```{=html}
<!-- -->
```
-   The translation should be performed accurately and efficiently to
    > minimize delays or errors.

```{=html}
<!-- -->
```
-   Subtitle Synchronization:

```{=html}
<!-- -->
```
-   The system is expected to exhibit consistent and reliable
    > performance, ensuring promptness in displaying translations upon
    > student access to the website, with an upper limit of 1 second.

-   The processing speed for submitting and executing Translator
    > operations should be swift, with an average response time for each
    > operation not exceeding 0.5 seconds.

```{=html}
<!-- -->
```
-   Subtitle Customization:

```{=html}
<!-- -->
```
-   Students should be able to toggle the display of subtitles on/off

```{=html}
<!-- -->
```
-   User Management:

```{=html}
<!-- -->
```
-   The system should provide user authentication and account creation
    > for students.

-   Each student should have a personal profile to track their document
    > history, preferred settings, and translation preferences.

```{=html}
<!-- -->
```
-   Performance and Reliability:

```{=html}
<!-- -->
```
-   The system should be responsive and provide fast document loading
    > times, ensuring smooth access to educational materials.

-   The system should be reliable, minimizing downtime and errors to
    > avoid disrupting students\' learning experience.

```{=html}
<!-- -->
```
-   Security:

```{=html}
<!-- -->
```
-   Stringent security measures are imperative to ensure the robust
    > protection of data, which is securely stored within a fortified
    > Database.

-   The implementation requires the utilization of API Keys or Tokens to
    > accurately authenticate and authorize access to, as well as
    > modification of, data reflected within the Database.

```{=html}
<!-- -->
```
-   Scalability:

```{=html}
<!-- -->
```
-   The system should be designed to handle a large number of students
    > and a growing library of documents.

-   It should be capable of scaling up its resources to accommodate
    > increased usage without compromising performance.

```{=html}
<!-- -->
```
-   Compatibility:

```{=html}
<!-- -->
```
-   It should work on popular web browsers to ensure widespread
    > accessibility.

```{=html}
<!-- -->
```
-   Support and Maintenance:

```{=html}
<!-- -->
```
-   The system should provide a support mechanism for students to report
    > issues or seek assistance.

-   Regular maintenance and updates should be performed to fix bugs, add
    > new features, and improve system performance.

# 

3.  # **Software architecture and design**

    1.  ## **Software architecture**

-   Client-Server architecture

-   Divide the system into two main components: the Client, which is the
    > Google Chrome browser extension, and the Server, which hosts the
    > application logic, database, and handles requests and responses.

> ![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image3.png){width="6.495494313210848in"
> height="3.4305555555555554in"}

-   Advantages of Client-Server Architecture for FUNiX Passport:

```{=html}
<!-- -->
```
-   Scalability: The client-server architecture allows for scalability
    > by separating the processing and data storage on the server-side,
    > making it easier to handle a large number of users and documents.

-   Security: By centralizing data and logic on the server, it becomes
    > easier to implement robust security measures, ensuring the privacy
    > and protection of user data and documents.

-   Performance: The server can perform computationally intensive tasks
    > like document translation, subtitle synchronization, and
    > processing video files, allowing the client-side to focus on
    > display and user interaction.

-   Compatibility: The client-server architecture is suitable for a
    > diverse user base as it supports different browsers, making it
    > accessible from various platforms.

    1.  ## **Usecase**

```{=html}
<!-- -->
```
-   Actors:

```{=html}
<!-- -->
```
-   User: Solely equipped with the ability to login and logout from the
    > application.

-   Translator: Linguistic experts are capable of executing the
    > following operations within the application:

```{=html}
<!-- -->
```
-   Upload the translated Vietnamese subtitle file

-   Upload translated Document file in Vietnamese

-   View the list of uploaded translation files

-   Download the translated file

-   Search for translations using filters

-   Delete subtitle files or documents

-   Edit information

```{=html}
<!-- -->
```
-   Administrator: Primarily entrusted with the responsibility of
    > overseeing user account management:

```{=html}
<!-- -->
```
-   Deletion of user accounts

-   Granting permissions to a user (transferring the role from User to
    > Translator)

-   Revoking permissions from a user (reverting the role from Translator
    > to User)

```{=html}
<!-- -->
```
-   Reviewer:

```{=html}
<!-- -->
```
-   Entrusted with the responsibility of meticulously assessing the
    > precision of the Translator\'s video translations and providing
    > constructive feedback

-   View the list of uploaded translation files

-   Search for translations using filters

-   Download the translated file

    1.  ### ***Usecase of User***

![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image6.png){width="6.495494313210848in"
height="2.1666666666666665in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Login                                                 |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Users can log in to the system and use the functions  |
| escription** | therein.                                              |
+--------------+-------------------------------------------------------+
| *            | User has not logged into the system                   |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. User accesses the management website. Click on    |
| Mainstream** | \"Login\"                                             |
|              |                                                       |
|              | 2\. The system displays the Login Form.               |
|              |                                                       |
|              | 3\. User enters login information.                    |
|              |                                                       |
|              | 4\. If the login information is correct, update the   |
|              | information into the system.                          |
|              |                                                       |
|              | 5\. User request the transcription                    |
+--------------+-------------------------------------------------------+
| **Secondary  | In step 4, if the login information is incorrect, a   |
| stream**     | notification will be displayed to the user.           |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Logout                                                |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Users can log out after using the system.             |
| escription** |                                                       |
+--------------+-------------------------------------------------------+
| *            | User has logged into the system                       |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. User accesses the control panel. Click on \"Log   |
| Mainstream** | out\"                                                 |
|              |                                                       |
|              | 2\. The system logs out and displays the Login Form.  |
+--------------+-------------------------------------------------------+
| **Secondary  |                                                       |
| stream**     |                                                       |
+--------------+-------------------------------------------------------+

### ***Usecase of Translator***

![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image10.png){width="5.989583333333333in"
height="8.447916666666666in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Upload translations                                   |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Translator can attach the translated subtitle file or |
| escription** | document to the system                                |
+--------------+-------------------------------------------------------+
| *            | Translator has logged into the system                 |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Translator accesses the management page. Click on |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Translator click on "Upload translation"          |
|              |                                                       |
|              | 3\. The system displays two options: "Upload          |
|              | subtitle" and "Upload document"                       |
|              |                                                       |
|              | 4\. Translator choose "Upload subtitle"               |
|              |                                                       |
|              | 5\. System allows translator to upload subtitle and   |
|              | displays status (Successful, Error, Uploading)        |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 4, if the translator choose "Upload        |
| stream**     | document"                                             |
|              |                                                       |
|              | 5\. System allows translator to upload document and   |
|              | display status (Successful, Error, Uploading)         |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | View translations                                     |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Translator can view subtitle translations or document |
| escription** | translations                                          |
+--------------+-------------------------------------------------------+
| *            | Translator has logged into the system                 |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Translator accesses the management page. Click on |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Translator clicks on "View translations"          |
|              |                                                       |
|              | 3\. The system displays two options: "View subtitles" |
|              | and "View documents"                                  |
|              |                                                       |
|              | 4\. Translator chooses "View subtitles"               |
|              |                                                       |
|              | 5\. System displays a list of subtitles               |
|              |                                                       |
|              | 6\. Translator clicks on one of the subtitles         |
|              |                                                       |
|              | 7\. System displays that subtitle                     |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 4, if the translator chooses "View         |
| stream**     | documents"                                            |
|              |                                                       |
|              | 5\. System displays a list of documents               |
|              |                                                       |
|              | 6\. Translator clicks on one of the documents         |
|              |                                                       |
|              | 7\. System displays that documents                    |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Download translations                                 |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Translator can download subtitle translation or       |
| escription** | document translation                                  |
+--------------+-------------------------------------------------------+
| *            | Translator has logged into the system                 |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Translator accesses the management page. Click on |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Translator click on "Download translation"        |
|              |                                                       |
|              | 3\. The system displays two options: "Download        |
|              | subtitle" and "Download document"                     |
|              |                                                       |
|              | 4\. Translator choose "Download subtitles"            |
|              |                                                       |
|              | 5\. System displays a list of subtitles               |
|              |                                                       |
|              | 6\. Translator clicks on one of the subtitles         |
|              |                                                       |
|              | 7\. System allows translator to download that         |
|              | subtitle and displays status (Successful, Error,      |
|              | Downloading)                                          |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 4, if the translator choose "Download      |
| stream**     | documents"                                            |
|              |                                                       |
|              | 5\. System displays a list of documents               |
|              |                                                       |
|              | 6\. Translator clicks on one of the documents         |
|              |                                                       |
|              | 7\. System allows translator to download that         |
|              | document and displays status (Successful, Error,      |
|              | Downloading)                                          |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Search for translations                               |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Search for translation by filtering translation's     |
| escription** | identity                                              |
+--------------+-------------------------------------------------------+
| *            | Translator has logged into the system                 |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Translator accesses the management page. Click on |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Translator clicks on "View translations"          |
|              |                                                       |
|              | 3\. The system displays two options: "View subtitles" |
|              | and "View documents"                                  |
|              |                                                       |
|              | 4\. Translator chooses "View subtitles"               |
|              |                                                       |
|              | 5\. System displays a list of subtitles               |
|              |                                                       |
|              | 6\. Translator clicks on "Search" and System displays |
|              | filters                                               |
|              |                                                       |
|              | 7\. Translator enters Video Name, Video URL, Course   |
|              | ID, Video ID                                          |
|              |                                                       |
|              | 8\. System displays the found video. Display "Not     |
|              | found" if there is no corresponding video             |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 4, if the translator chooses "View         |
| stream**     | documents"                                            |
|              |                                                       |
|              | 5\. System displays a list of documents               |
|              |                                                       |
|              | 6\. Translator clicks on "Search" and System displays |
|              | filters                                               |
|              |                                                       |
|              | 7\. Translator enters Document Name, Document URL     |
|              |                                                       |
|              | 8\. System displays the found document . Display "Not |
|              | found" if there is no corresponding document          |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Delete translations                                   |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Translator can delete subtitle files or documents     |
| escription** |                                                       |
+--------------+-------------------------------------------------------+
| *            | Translator has logged into the system                 |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Translator accesses the management page. Click on |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Translator clicks on "View translations"          |
|              |                                                       |
|              | 3\. The system displays two options: "View subtitles" |
|              | and "View documents"                                  |
|              |                                                       |
|              | 4\. Translator chooses "View subtitles"               |
|              |                                                       |
|              | 5\. System displays a list of subtitles               |
|              |                                                       |
|              | 6\. Translator searches for a existing subtitle using |
|              | filters                                               |
|              |                                                       |
|              | 7\. System displays that subtitle                     |
|              |                                                       |
|              | 8\. Translator clicks on "Delete"                     |
|              |                                                       |
|              | 9\. System deletes the subtitle and displays status   |
|              | (Successful, Error, Deleting)                         |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 4, if the translator choose "View          |
| stream**     | documents"                                            |
|              |                                                       |
|              | 5\. System displays a list of documents               |
|              |                                                       |
|              | 6\. Translator searches for a existing document using |
|              | filters                                               |
|              |                                                       |
|              | 7\. System displays that document                     |
|              |                                                       |
|              | 8\. Translator clicks on "Delete"                     |
|              |                                                       |
|              | 9\. System deletes the document and displays status   |
|              | (Successful, Error, Deleting)                         |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Edit information                                      |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Translator can edit information of the translation    |
| escription** |                                                       |
+--------------+-------------------------------------------------------+
| *            | Translator has logged into the system                 |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Translator accesses the management page. Click on |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Translator clicks on "View translations"          |
|              |                                                       |
|              | 3\. Translator searches for a translation using       |
|              | filters. It can be a subtitle or a document           |
|              |                                                       |
|              | 4\. System displays the translation                   |
|              |                                                       |
|              | 5\. Translator clicks on "Info" and system displays   |
|              | the metadata of the translation                       |
|              |                                                       |
|              | 6\. Translator clicks on "Edit" and system displays   |
|              | two options: "Edit metadata" and "Re-upload a         |
|              | different translation"                                |
|              |                                                       |
|              | 7\. Translator chooses "Edit metadata" and system     |
|              | allows translator to edit it                          |
|              |                                                       |
|              | 8\. After editing, translator clicks on "Save"        |
|              |                                                       |
|              | 9\. System saves the changes and displays status      |
|              | (Changes saved successfully or Changes saved          |
|              | unsuccessfully)                                       |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 7, if the translator chooses "Re-upload a  |
| stream**     | different translation".                               |
|              |                                                       |
|              | 8\. System allows translator to upload translation    |
|              | and display status (Successful, Error, Uploading)     |
+--------------+-------------------------------------------------------+

### ***Usecase of Reviewer***

![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image1.png){width="6.495494313210848in"
height="5.333333333333333in"}

+--------------+-------------------------------------------------------+
| **Use Case   | View translations                                     |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Reviewer can view subtitle translations or document   |
| escription** | translations                                          |
+--------------+-------------------------------------------------------+
| *            | Reviewer has logged into the system                   |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Reviewer accesses the management page. Click on   |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Reviewer clicks on "View translations"            |
|              |                                                       |
|              | 3\. The system displays two options: "View subtitles" |
|              | and "View documents"                                  |
|              |                                                       |
|              | 4\. Reviewer chooses "View subtitles"                 |
|              |                                                       |
|              | 5\. System displays a list of subtitles               |
|              |                                                       |
|              | 6\. Reviewer clicks on one of the subtitles           |
|              |                                                       |
|              | 7\. System displays that subtitle                     |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 4, if the reviewer chooses "View           |
| stream**     | documents"                                            |
|              |                                                       |
|              | 5\. System displays a list of documents               |
|              |                                                       |
|              | 6\. Reviewer clicks on one of the documents           |
|              |                                                       |
|              | 7\. System displays that documents                    |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Download translations                                 |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Reviewer can download subtitle translation or         |
| escription** | document translation                                  |
+--------------+-------------------------------------------------------+
| *            | Reviewer has logged into the system                   |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Reviewer accesses the management page. Click on   |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Reviewer click on "Download translation"          |
|              |                                                       |
|              | 3\. The system displays two options: "Download        |
|              | subtitle" and "Download document"                     |
|              |                                                       |
|              | 4\. Reviewer choose "Download subtitles"              |
|              |                                                       |
|              | 5\. System displays a list of subtitles               |
|              |                                                       |
|              | 6\. Reviewer clicks on one of the subtitles           |
|              |                                                       |
|              | 7\. System allows reviewer to download that subtitle  |
|              | and displays status (Successful, Error, Downloading)  |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 4, if the reviewer choose "Download        |
| stream**     | documents"                                            |
|              |                                                       |
|              | 5\. System displays a list of documents               |
|              |                                                       |
|              | 6\. Reviewer clicks on one of the documents           |
|              |                                                       |
|              | 7\. System allows reviewer to download that document  |
|              | and displays status (Successful, Error, Downloading)  |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Search for translations                               |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Search for translation by filtering translation's     |
| escription** | identity                                              |
+--------------+-------------------------------------------------------+
| *            | Reviewer has logged into the system                   |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Reviewer accesses the management page. Click on   |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Reviewer clicks on "View translations"            |
|              |                                                       |
|              | 3\. The system displays two options: "View subtitles" |
|              | and "View documents"                                  |
|              |                                                       |
|              | 4\. Reviewer chooses "View subtitles"                 |
|              |                                                       |
|              | 5\. System displays a list of subtitles               |
|              |                                                       |
|              | 6\. Reviewer clicks on "Search" and System displays   |
|              | filters                                               |
|              |                                                       |
|              | 7\. Reviewer enters Video Name, Video URL, Course ID, |
|              | Video ID                                              |
|              |                                                       |
|              | 8\. System displays the found video. Display "Not     |
|              | found" if there is no corresponding video             |
+--------------+-------------------------------------------------------+
| **Secondary  | \- In step 4, if the reviewer chooses "View           |
| stream**     | documents"                                            |
|              |                                                       |
|              | 5\. System displays a list of documents               |
|              |                                                       |
|              | 6\. Reviewer clicks on "Search" and System displays   |
|              | filters                                               |
|              |                                                       |
|              | 7\. Reviewer enters Document Name, Document URL       |
|              |                                                       |
|              | 8\. System displays the found document . Display "Not |
|              | found" if there is no corresponding document          |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Providing feedback                                    |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Reviewer can providing constructive feedback for the  |
| escription** | translator about the transcription                    |
+--------------+-------------------------------------------------------+
| *            | Reviewer has logged into the system                   |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Reviewer accesses the management page. Click on   |
| Mainstream** | "Translations" in the control panel                   |
|              |                                                       |
|              | 2\. Reviewer clicks on "View translations"            |
|              |                                                       |
|              | 3\. Reviewer searches for a translation using         |
|              | filters. It can be a subtitle or a document           |
|              |                                                       |
|              | 4\. System displays the translation                   |
|              |                                                       |
|              | 5\. Reviewer clicks on "Send feedback" and system     |
|              | allows reviewer to enter feedback                     |
|              |                                                       |
|              | 6\. After the feedback was sent, system displays      |
|              | status (Feedback sent successfully, Feedback sent     |
|              | unsuccessfully)                                       |
+--------------+-------------------------------------------------------+
| **Secondary  |                                                       |
| stream**     |                                                       |
+--------------+-------------------------------------------------------+

### ***Usecase of Administrator***

![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image8.png){width="6.495494313210848in"
height="2.0555555555555554in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Deletion of user accounts                             |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Administrator can delete user accounts                |
| escription** |                                                       |
+--------------+-------------------------------------------------------+
| *            | Administrator has logged into the system              |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Administrator accesses the management page. Click |
| Mainstream** | on "Manage accounts" in the control panel             |
|              |                                                       |
|              | 2\. System displays account list                      |
|              |                                                       |
|              | 3\. Administrator clicks on one of the accounts       |
|              |                                                       |
|              | 4\. System displays three options: "Delete", "Make    |
|              | Translator", "Make User"                              |
|              |                                                       |
|              | 5\. Administrator clicks on "Delete"                  |
|              |                                                       |
|              | 6\. System deletes the account and displays status    |
|              | (Changes saved successfully or Changes saved          |
|              | unsuccessfully)                                       |
+--------------+-------------------------------------------------------+
| **Secondary  |                                                       |
| stream**     |                                                       |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Granting permissions to a user                        |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Administrator can change role from User to Translator |
| escription** |                                                       |
+--------------+-------------------------------------------------------+
| *            | Administrator has logged into the system              |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Administrator accesses the management page. Click |
| Mainstream** | on "Manage accounts" in the control panel             |
|              |                                                       |
|              | 2\. System displays account list                      |
|              |                                                       |
|              | 3\. Administrator clicks on one of the accounts       |
|              |                                                       |
|              | 4\. System displays three options: "Delete", "Make    |
|              | Translator", "Make User"                              |
|              |                                                       |
|              | 5\. Administrator clicks on "Make Translator"         |
|              |                                                       |
|              | 6\. System grants permissions to the account and      |
|              | displays status (Changes saved successfully or        |
|              | Changes saved unsuccessfully)                         |
+--------------+-------------------------------------------------------+
| **Secondary  |                                                       |
| stream**     |                                                       |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Revoking permissions from a user                      |
| Name**       |                                                       |
+==============+=======================================================+
| **D          | Administrator can change role from Translator to User |
| escription** |                                                       |
+--------------+-------------------------------------------------------+
| *            | Administrator has logged into the system              |
| *Condition** |                                                       |
+--------------+-------------------------------------------------------+
| **           | 1\. Administrator accesses the management page. Click |
| Mainstream** | on "Manage accounts" in the control panel             |
|              |                                                       |
|              | 2\. System displays account list                      |
|              |                                                       |
|              | 3\. Administrator clicks on one of the accounts       |
|              |                                                       |
|              | 4\. System displays three options: "Delete", "Make    |
|              | Translator", "Make User"                              |
|              |                                                       |
|              | 5\. Administrator clicks on "Make User"               |
|              |                                                       |
|              | 6\. System revokes permissions from the account and   |
|              | displays status (Changes saved successfully or        |
|              | Changes saved unsuccessfully)                         |
+--------------+-------------------------------------------------------+
| **Secondary  |                                                       |
| stream**     |                                                       |
+--------------+-------------------------------------------------------+

## **Usecase of the System**

![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image2.png){width="3.8854166666666665in"
height="8.489583333333334in"}

## **Class Diagram**

![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image5.png){width="6.495494313210848in"
height="3.611111111111111in"}

## **Sequence Diagram**

![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image7.png){width="6.495494313210848in"
height="6.083333333333333in"}

## **Activity Diagram**

![](vertopal_4855b31bbbff49be9216b6ab65abf55b/media/image9.png){width="3.1145833333333335in"
height="8.083333333333334in"}
