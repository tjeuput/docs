Infoskop-Base 5.0.0: Focus on Efficiency, Control, and Reliability

This major release provides critical updates that streamline your daily tasks, give you greater administrative control, and significantly improve the stability of the entire system.

1. Improvements to Daily Workflow

These enhancements focus on making your communications, template use, and data visualization clearer and more effective.

Enhanced Email and Template Functionality

We have improved the reliability of email status notifications. Previously, the system sometimes displayed an email as "successfully sent" even if the configured SMTP server data was faulty or empty. Now, this issue is fixed, meaning **you will no longer receive a false success message** if your server configuration is incorrect.

When working within email and template texts, you now have **flexible options for handling images**. Users can adjust the size of embedded images using drag & drop, or by selecting preset sizes (50px, 75px, original size), or by defining custom dimensions. You can also easily add, edit, and remove links attached to these images.

A long-standing issue preventing links within emails, templates, and the Form Link Builder from opening in your local web browser has been resolved. **Links will now open correctly** as expected. (A minor adjustment was made to the Form Link Builder, requiring you to click the link directly for a preview).

For quicker workflow, the email icon now features a **dropdown arrow**, allowing you to instantly select a template before opening the main email window. This is available in the patient menu, Documents, and the Evaluation Cockpits.

Cockpit and Financial Accuracy

We have addressed an issue where the price transfer functionality in the PA and Bleaching Cockpits did not work correctly when the price included the Euro symbol (€). **Price transfers now function correctly**, regardless of the presence of the € symbol. Furthermore, we have updated and added **missing icons** to the PA and Bleaching Cockpits to ensure a complete visual experience.

2. Enhanced System Control and Administration

This release introduces deeper control over patient data and ensures system settings are consistently respected across the application.

Granular Patient Data Deletion

The process for deleting patient data has been adjusted and optimized. When initiating a deletion, you are presented with a dialog providing **granular control**. You can now select exactly which subsets of data you wish to remove, including Documents, History data, and Online data. You can also specify a **date limit** ("Only data up to and including").

This action is destructive, and the system requires a double confirmation and warns that **deleted data cannot be recovered**. If no date is specified, all data up to today will be deleted.

Reliable Online Function Deactivation

We have optimized the display and behavior when online functions are deactivated. Previously, even if online functions were disabled, certain menu entries were still accessible, and emails could still be sent from the patient file or via background processes.

Now, the system is consistent: when online functions are deactivated, **all related menu entries and email icons throughout the application (including in the patient file and cockpits) are locked, disabled, and grayed out**, ensuring the deactivation is properly respected across the entire system.

Optimized Administrative Settings

The display behavior for making **bulk edits in the warning settings has been improved**. This is especially helpful when switching between views like "Warnings," "History," and "All," and when using the "All Yes/No" options. Additionally, the license query for the **::ORA reply function** has been fixed, and the reply function is now only active for customers who use ::ORA; for all others, the function is deactivated and the display adjusted.

3. Increased Stability, Performance, and New Tools

These crucial updates ensure that the underlying technical components are more robust, self-healing, and compatible with modern systems.

Introducing ::LEA and Performance Enhancements

We are introducing a completely **new product: Leistungserfassung (::LEA)**, which is now available. Licensing for ::LEA occurs automatically upon correct setup.

For processes that require slightly longer loading times—such as opening the infoskop-Monitor or the new ::LEA application—users will now see a **"Please wait..." display** ("Bitte warten …"), making the process transparent and assuring the user that the system is actively working.

Self-Healing and Error Prevention

The **Starter.exe** component is now equipped with a new function to **automatically monitor its own functionality**. If the main Base service becomes unresponsive (for instance, while processing a very large document), the Starter will **independently restart the service**. This new feature avoids interruptions and prevents the system from hanging, eliminating the need for manual restarts.

We have also addressed system communication issues:

• **Clean Server Shutdown (HL7):** HL7 servers are now automatically monitored. When the Base-Starter shuts down, the HL7 server closes its service **"softly"**. This prevents network problems and long waiting times (timeouts).

• **Improved Partner Connection (Evident):** A fix ensures that the extended interface with Evident Version 6 now **automatically recognizes and configures itself correctly**. This removes the need for technical support intervention to manually configure the connection.

• **Logging Improvements:** In case of errors, the Starter now logs its attempts to reach the Base service in the `report.dat` file. This information is transferred to Logcheck, making error analysis significantly easier.

Modern System Requirements and Installation

To ensure performance and maintain current standards, the installation file for **Bonjour 32 Bit has been removed**. The product now **only supports 64-Bit and ARM systems**. There is now a second 64-bit Bonjour installation file that supports both Intel and ARM architectures.

For environments running multiple Base services on one machine, the default service name is no longer assigned automatically to prevent conflicts. The Updater can now accept specific service names for correct stopping and starting of services. Finally, an issue where multiple identical update screens (splash screens) appeared simultaneously during installation has been fixed, so **only one screen is shown per execution**.