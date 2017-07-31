alfviral (Alfresco Virus Alert)
===============================

Alfresco's Module for Enterprise and Community versions to scan documents using every antivirus engine. Verifying documents with ClamAV, Symantec, McAfee, Sophos, [...] using some mechanisms as sending datastream to a TCP port, execute command with parameters, sending to www.virustotal.com or using ICAP protocol.

Features:
  - Detection through 4 modes (for command, clamav data stream, http for virustotal.com and ICAP protocol)
  - Use of "policies" to scan uploaded and/or read content
  - Use of "scheduler" to scan spaces/folders programmatically
  - Use of action "scan" in user interfaces (Explorer and Share)
  - File exceptions
  - Notification by email
  - Assignment of "aspects" (subtypes) to classify infections
  - ICAP (Internet Content Adaptation Protocol) for scanning many antivirus engines: Symantec, McAfee, Sophos, ...
  - Email notify to user and admin in case of infection
  - Arquitecture has service: AntivirusService
  
For 4.2.x before versions go to https://code.google.com/p/alfviral/

Alfresco Summit 2013: https://github.com/fegorama/alfviral/blob/master/docs/Alfviral_Alfresco_Summit_2013_v1.pdf

### Config global properties

```
# Command to exec, i.e. clamscan, alfviral.sh, etc. (COMMAND)
alfviral.command.exec=C\:\\Users\\fegor\\Documents\\alfviral.bat

# Config for ClamAV in stream data (INSTREAM)
alfviral.instream.timeout=30000
alfviral.instream.host=192.168.56.101
alfviral.instream.port=3310
alfviral.instream.chunkSize=1024

# Config for VIRUSTOTAL
alfviral.vt.key=
alfviral.vt.url=https://www.virustotal.com/vtapi/v2/file/scan

# Config for ICAP protocol
alfviral.icap.host=192.168.56.101
alfviral.icap.port=1344
alfviral.icap.service=srv_clamav

# Modes: COMMAND, INSTREAM, VIRUSTOTAL, ICAP
alfviral.mode=ICAP

# Events
alfviral.on_update=TRUE
alfviral.on_read=FALSE

# Scheduled action
alfviral.scheduled.pathQuery=/app:company_home/st:sites
alfviral.scheduled.cronExpression=* * * * * ? 2099

# List of file only or exceptions
alfviral.file.exceptions=text/html|text/xml|application/pdf|image/jpeg|image/png|image/giftext/plain
alfviral.file.only=application/octet-stream|application/x-dosexec|application/bat|application/x-bat|application/x-msdos-program|application/textedit|application/cmd|application/x-ms-dos-executable
alfviral.file.only_or_exceptions=exceptions

# Notification of infected
# Options: Notify to user to upload file and notify to admin. Use email config in profile (people)
alfviral.notify.user=true
alfviral.notify.admin=true
alfviral.notify.toUser=
alfviral.notify.user.template=notify_user_en.html.ftl
alfviral.notify.admin.template=notify_user_en.html.ftl
```

