---
layout: page
title: Setup
---

This workshop was designed by datacarpentry to be run on pre-imaged Amazon Web Services 
(AWS) instances. For information about how to
use the workshop materials, see the 
[setup instructions](https://www.datacarpentry.org/genomics-workshop/setup.html) on the main workshop page.

At Utrecht University form 2024 we are using a preconfigured linux server (gemini.science.uu.nl) and have provided required files in 
- `HOME/course_data` and
- presentations in `HOME/course_content`

On your **personal machine** you require some software to open/edit files and connect to the gemini server:
- A spreadsheet program (Excel, LibreOffice (free), or something similar)
- A terminal to connect a secure shell. On windows you can use mobaXterm, putty, gitbash, or the powershell. Mac has its own terminal.
- A file transfer program using sftp. You can use winSCP, filezilla or something similar. This is convenient to (re)organise your files oor edit scripts/files in a graphical interface.
- An advanced text/script editor might be helpfull. On windows notepad++ is commonly used. On other platforms sublimetext or build-in editors.

**To connect to the UU gemini server:**
- Terminal: `ssh your_solisid@gemini.science.uu.nl`
  + Login using your solis credentials
  + Setting the (conda) environment command `course B-MBIMIGE`
- **S**ecure **F**ile **T**ransfer: `sftp gemini.science.uu.nl`

🟢 It first login you can be prompted for allowing the secure shell access (fingerprint). Just accept this after checking that the gemini.science.uu.nl URL is correct.

When you login gemini using the terminal and start the course conda environment you should see something similar to below:
![image](https://github.com/user-attachments/assets/998ac1d4-2b7a-4fa1-92fe-d17ca938437b)

When you connect using a file browser like WinSCP:
![image](https://github.com/user-attachments/assets/22971006-a5aa-42b2-a409-99c0c672e1c0)

From there you can also directly open/inspect and edit (script) files...
![image](https://github.com/user-attachments/assets/5653d067-a6ff-4388-b2b5-03641d41b86b)
