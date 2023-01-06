# BlazeDS Turnkey Bundle Archive

Before Adobe donated BlazeDS to the [Apache Flex](https://flex.apache.org/) project, Adobe BlazeDS releases included a special "turnkey" bundle that included a pre-configured version of Apache Tomcat and a number of samples — to demonstrate how to use BlazeDS on the server with Apache Flex on the client.

Adobe no longer makes this turnkey bundle available for download. However, because the bundle was released under an open source license, this archive was created to ensure that its included sample applications remain available as a reference for learning purposes.

> **Warning!** This bundle contains the original (now outdated) versions of Adobe BlazeDS 4.0.0.14931 and Apache Tomcat 6.0.14. These should not be used in production, as they may contain security vulnerabilities. For real-world apps, you should upgrade to the latest versions of BlazeDS and Tomcat.

## What is BlazeDS?

BlazeDS is the server-based Java remoting and web messaging technology that enables developers to easily connect to back-end distributed data and push data in real-time to front-end applications for more responsive rich web application experiences.

BlazeDS uses AMF (Action Message Format), a form of binary encoding to serialize Java object graphs on the remote server and transfer them to the client (which may be written in JavaScript or another language) to be deserialized, reproducing the same object graph that exists on the server. One of the advantages of AMF is being able to serialize the data in a more compact way than common plain text data formats, like JSON or XML, which means that sending AMF data over a network requires less bandwidth.

## Is Adobe Flash Player required?

The original front-end sample Flex applications included in this bundle require the Adobe Flash Player plugin to run. As of 2020, Adobe has discontinued Flash Player updates, and they no longer make old versions of the plugin available for download. Additionally, most web browsers have completely removed support for displaying content using plugins.

However, these front-end samples have been recreated to be run using JavaScript, without a plugin.

The [_feathersui-blazeds-turnkey-samples_](https://github.com/feathersui/feathersui-blazeds-turnkey-samples) repository includes recreations of a number of the front-end samples from the BlazeDS Turnkey bundle using the [Haxe](https://haxe.org/) programming language, and the [Feathers UI](https://feathersui.com/) library. These new samples can be compiled to HTML and JavaScript, allowing them to replace the original Flex front-end samples.

## Upgrade Tomcat

The original bundle includes Apache Tomcat 6.0.14, which may not be fully compatible with modern environments. Before getting started, you may need to upgrade Tomcat to a newer version.

### Tomcat 9

The existing samples are compatible with [Tomcat 9](https://tomcat.apache.org/download-90.cgi). Follow these steps to upgrade.

1. Delete everything except the _webapps_ subdirectory inside the _tomcat_ directory of the extracted BlazeDS Turnkey bundle.
1. Download a [Tomcat 9 binary distribution](https://tomcat.apache.org/download-90.cgi) for your operating system.
1. Extract the Tomcat binary distribution somewhere on your computer.
1. Copy everything except the _webapps_ subdirectory from the extracted Tomcat binary distribution to the _tomcat_ directory of the extracted BlazeDS Turnkey bundle.

### Tomcat 10

Upgrading to [Tomcat 10](https://tomcat.apache.org/download-10.cgi) or newer requires one additional step because the existing samples need to be migrated from Java EE to Jakarta EE, as explained in the [Tomcat 10 Migration Guide](https://tomcat.apache.org/migration-10.html). Thankfully, most of the work is done by an automated tool built into Tomcat.

1. Delete everything except the _webapps_ subdirectory inside the _tomcat_ directory of the extracted BlazeDS Turnkey bundle.
1. Rename the existing _webapps_ subdirectory to _webapps-javaee_. This will cause the automated migration process to trigger when you start the server.
1. Download a [Tomcat 10 binary distribution](https://tomcat.apache.org/download-10.cgi) for your operating system.
1. Extract the Tomcat binary distribution somewhere on your computer.
1. Copy everything except the _webapps_ subdirectory from the extracted Tomcat binary distribution to the _tomcat_ directory of the extracted BlazeDS Turnkey bundle.

> After successfully starting the Tomcat server, you can delete the _webapps-javaee_ directory.

## Usage

Follow these steps to start a local development server.

1. Download and extract [_blazeds-turnkey-4.0.0.14931.zip_](https://github.com/joshtynjala/blazeds-turnkey-archive/releases/tag/v4.0.0.14931).
1. Upgrade the bundled Tomcat server using the appropriate instructions above.
1. Open a terminal, and navigate to the directory where the BlazeDS Turnkey bundle was extracted.
1. Use the provided startup script to start Tomcat.

   On Windows, run **.\tomcat\bin\startup.bat**

   On macOS or Linux, run  **./tomcat/bin/startup.sh**
1. If the server started successfully, you should see the text _Tomcat started._ in the terminal output.
1. Open a web browser, and navigate to the following URL: _http://localhost:8080/samples/_ to see a page explaining the BlazeDS samples.