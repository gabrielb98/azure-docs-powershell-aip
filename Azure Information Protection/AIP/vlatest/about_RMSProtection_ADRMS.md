```
TOPIC
    about_RMSProtection_ADRMS

SHORT DESCRIPTION 
    Information to get started with the RMS Protection tool for an organization
    that uses Active Directory Rights Management Services (AD RMS). 

LONG DESCRIPTION
    This topic describes how to start using the RMS Protection tool to protect
    or unprotect files if your organization uses AD RMS. The information
    includes:
        - Additional prerequisites that are specific to AD RMS
        - Using RMS Protection cmdlets - example scenarios

  PREREQUISITES 
      In addition to any prerequisites for the RMS Protection tool (see 
      RMS Protection Cmdlets on MSDN 
      - https://msdn.microsoft.com/library/azure/mt433195.aspx) there is one
      additional prerequisite for AD RMS: 

      * Read and Execute permissions on ServerCertification.asmx

      To run these cmdlets for AD RMS, your account must have
      Read and Execute permissions to access ServerCertification.asmx:

        1. Log on to an AD RMS server
        2. Click Start, and then click Computer.
        3. In File Explorer, navigate to
           %systemdrive%\Initpub\wwwroot\_wmsc\Certification
        4. Right-click ServerCertification.asmx, then click Properties.
        5. In the ServerCertification.asmx Properties dialog box,
           click the Security tab. 
        6. Click the Continue button or the Edit Button. 
        7. In the Permissions for ServerCertification.asmx dialog box,
           click Add. 
        8. Add your account name. If other AD RMS administrators will also
           use these cmdlets to protect and unprotect files, add their names
           as well. 
        9. In the Allow column, make sure that the Read and Execute, and 
           the Read checkboxes are selected. 
        10.Click OK twice.

  USING RMS PROTECTION CMDLETS - EXAMPLE SCENARIOS
      A typical scenario for these cmdlets is to protect all files in a folder
      by using a rights policy template, or to unprotect a file. 

      First, if you have more than one deployment of AD RMS, you will need the
      names of your AD RMS servers, which you do by using the Get-RMSServer
      cmdlet to display a list of available servers:
    
          C:\PS> Get-RMSServer

          Number of RMS Servers that can provide templates: 2 
          ConnectionInfo             DisplayName          AllowFromScratch
          --------------             -------------        ----------------
          Microsoft.InformationAnd…  RmsContoso                       True
          Microsoft.InformationAnd…  RmsFabrikam                      True

      Before you can protect files, you need to get a list of RMS templates to 
      identify which one to use and its corresponding ID number. Only when you
      have more than one AD RMS deployment will you need to specify the 
      RMS server as well. 
      From the output, you can then copy the template ID:

          C:\PS>Get-RMSTemplate -RMSServer RmsContoso

           TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
           CultureInfo       : en-US
           Description       : This content is proprietary information intended for 
                               internal users only. This content cannot be modified.
           Name              : Contoso, Ltd - Confidential View Only
           IssuerDisplayName : Contoso, Ltd
           FromTemplate      : True


           TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
           CultureInfo       : en-US
           Description       : This content is proprietary information intended for 
                               internal users only. This content can be modified but 
                               cannot be copied and printed.
           Name              : Contoso, Ltd - Confidential
           IssuerDisplayName : Contoso, Ltd
           FromTemplate      : True
           FromTemplate      : True

      Now you know the template ID, you can use it with the Protect-RMSFile
      cmdlet to protect a single file or all files in a folder. For example, if
      you want to protect a single file only and replace the original, by 
      using the "Contoso, Ltd - Confidential" template:

          C:\PS>Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

          InputFile             EncryptedFile
          ---------             -------------
          C:\Test.docx          C:\Test.docx   
 
      To protect all files in a folder, use the -Folder parameter with a 
      drive letter and path, or UNC path. For example:

          C:\PS>Protect-RMSFile -Folder \\Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

          InputFile                          EncryptedFile
          ---------                          -------------
          \\Server1\Documents\Test1.docx     \\Server1\Documents\Test1.docx   
          \\Server1\Documents\Test2.docx     \\Server1\Documents\Test2.docx   
          \\Server1\Documents\Test3.docx     \\Server1\Documents\Test3.docx   
          \\Server1\Documents\Test4.docx     \\Server1\Documents\Test4.docx   

      When the file name extension does not change after RMS protection is
      applied, you can always use the Get-RMSFileStatus cmdlet later to check
      whether the file is protected. For example: 

          C:\PS>Get-RMSFileStatus -File \\Server1\Documents\Test1.docx

          FileName                              Status
          --------                              ------
          \\Server1\Documents\Test1.docx         Protected

      To unprotect a file, you must have Owner or Extract rights from when the
      file was protected, or be super user for AD RMS. Then, use the Unprotect cmdlet. 
      For example:

          C:\PS> Unprotect-RMSFile C:\test.docx -InPlace

          InputFile                             DecryptedFile
          ---------                             -------------
          C:\Test.docx                          C:\Test.docx

   Not all the cmdlets in the RMS Protection module are applicable for AD RMS.
   The applicable cmdlets are Get-RMSFileStatus, Get-RMSServer,
   Get-RMSTemplate, New-RMSProtectionLicense, Protect-RMSFile, 
   and Unprotect-RMSFile. The cmdlets that are not applicable for AD RMS are
   Get-RMSServerAuthentication, Set-RMSServerAuthentication, Clear-RMSAuthentication.


   For more information about any of the RMS Protection module cmdlets,
   use the Get-Help <cmdlet name> cmdlet, where <cmdlet name> is the 
   name of the cmdlet that you want to research. For example:
       C:\PS> Get-Help Get-RMSServer


SEE ALSO
    Get-RMSFileStatus
    Get-RMSServer
    Get-RMSTemplate
    Get-RMSFileStatus
    Protect-RMSFile
    Unprotect-RMSFile
```