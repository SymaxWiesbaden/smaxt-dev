## Installing the smaxt PowerPoint add-in

With the smaxt PowerPoint add-in, you can easily design al layout for a PPTX- documents to be produced in your database with smaxt. Placeholders, data blocks and parameters can be inserted into a PowerPoint document. Alle elements can be formatted with default PowerPoint functionality. The AddIn also allows you to insert diagrams based on smaxt data modules.

### System Requirements

The smaxt PowerPoint add-in requires Microsoft PowerPoint™ 2010 or higher. Furthermore, the .NET Framework 4.56 and the Visual Studio Tools for Office 2010 Runtime \(VSTO\)[^1] are required. Minimum 20 MB of free space is required for the application files.

### Download and Installation

#### 1. Download

Download the setup program from www.smaxt.com `Setup_smaxt_PowerPoint_Add-In_V3.0_en.zip` or detach the installer from the e-mail you received together with the license information. Copy the file to a directory on the target machine.

#### 2. Unzip the archive

Open a command line and unzip the archive with the command:

`Unzip setup_smaxt_Excel_Add-In_V3.0_en.zip`

#### 3. Install the Add-In

First quit all currently running instances of Excel. Then run the setup-routine from the folder where you unzipped the archive and follow the on-screen instructions.

**Note:**

> The installer checks, if the required .NET-Framework is already installed on the target computer. If not, a dialogue prompts you to decide to either cancel installation or try to install the required .NET-Framework automatically. Keep in mind, that after .NET installation, a reboot of the computer is absolutely necessary, otherwise the smaxt-application will not work properly.  
>   
> Furthermore, the installation program checks whether the required version of the VSTO runtime is present on the target computer. If this is not the case, a dialog is displayed in which the installation can be either aborted or the required VSTO installation package can be downloaded and executed automatically.  
>   
> If you install the add-in without having installed the prerequisites prior, it can cause a deactivation of the add-in. In this case install the prerequisites and then reactivate the add-in as described in chapter "7.6.2.1 add-in is not activated".  
>   
> It has been observed that the detection of the required VSTO packet is not always reliable. In such cases, the smaxt add-in will show the following error message "... the manifest may not be valid or the file could not be downloaded ..." In this case, you have to manually download and install the VSTO-package.

After successful installation Excel starts with an additional ribbon entry labeled "smaxt". The smaxt-specific operations can now be carried out within Excel. For a first introduction to this add-in, see chapter "Getting Started".

[^1]: Download VSTO for Office 2010 at [http://www.microsoft.com/de-DE/download/details.aspx?id=48217](/Download der VSTO für Office 2010: http://www.microsoft.com/de-DE/download/details.aspx?id=48217)

