# Distributing IPA File with GitHub

## Introduction

This document outlines the process of distributing an IPA (iOS App Store Package) file using GitHub. Distributing your IPA file through GitHub is a great way to share your iOS app with testers, clients, or collaborators for testing purposes. By utilizing GitHub's version control and collaboration features, you can efficiently manage and distribute your app.

## Prerequisites

Before you begin, make sure you have the following:

- **GitHub Account**: You need an active GitHub account to create repositories and manage your code.
- **IPA File**: Generate an IPA file of your iOS app using Xcode or other suitable tools.
- **GitHub Repository**: Set up a GitHub repository where you intend to distribute the IPA file. This repository can be either private or public.

## Procedure

### 1. Build a New Release

1. Change the app versions accordingly and Build new ipa file using Xcode.
2. Get the ipa file and manifest.plist files.

### 2. Release Information

1. **Tag Version**: Assign a version number or tag for your release (e.g., v1.0.0).
2. **Release Title**: Provide a clear and descriptive title for the release.
3. **Description**: Write a release description that offers context about the IPA file, including changes, features, and any necessary instructions.

### 3. Upload IPA File

1. Create a directory within the repository's `IPAs` directory using the version name (e.g., `IPAs/v1.0.0`).
2. Upload the IPA file into the newly created directory.
3. Get the raw file link of the uploaded IPA file.

### 4. Create Manifest File

1. Create a `manifest.plist` file with the necessary app information. You can use a template like the following:
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
       <key>items</key>
       <array>
           <dict>
               <key>assets</key>
               <array>
                   <dict>
                       <key>kind</key>
                       <string>software-package</string>
                       <key>url</key>
                       <string>URL_TO_RAW_IPA_FILE</string>
                   </dict>
               </array>
               <key>metadata</key>
               <dict>
                   <key>bundle-identifier</key>
                   <string>YOUR_BUNDLE_IDENTIFIER</string>
                   <key>bundle-version</key>
                   <string>YOUR_BUNDLE_VERSION</string>
                   <key>kind</key>
                   <string>software</string>
                   <key>title</key>
                   <string>APP_NAME</string>
               </dict>
           </dict>
       </array>
   </dict>
   </plist>
2. Paste the raw file link of the uploaded IPA file in the url field within the manifest.plist file.

### 5. Upload Manifest File
1. Upload the manifest.plist file to the same directory as the IPA file.
2. Get the raw file link of the uploaded manifest.plist file.

### 6. Share Release Link
1. Once the release is published, you'll see the release page displaying the release information along with the attached IPA and manifest files.
2. Copy the URL of the raw manifest.plist file.
3. Share the raw link with the testing group, accompanied by the pre-text:
```arduino
itms-services://?action=download-manifest&url=URL_TO_RAW_MANIFEST_FILE
```


### Tips and Best Practices
1. **Use Tags**: Employ version number tags to keep track of different app versions.
2. **Clear Descriptions**: Provide detailed and clear descriptions of releases, including changes and features.
3. **Test the Link**: Before sharing the link with others, confirm that the IPA file can be downloaded and installed successfully.
4. **Maintain IPA Security**: Exercise caution when sharing the release link with unauthorized individuals, as the IPA file contains your app's code and resources.
