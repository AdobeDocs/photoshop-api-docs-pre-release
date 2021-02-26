<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Public Beta](#public-beta)
- [Welcome to Photoshop APIs!](#welcome-to-photoshop-apis)
- [General Setup and Onboarding](#general-setup-and-onboarding)
  - [Authentication](#authentication)
    - [Overview](#overview)
    - [Internal Adobe Users Only](#internal-adobe-users-only)
      - [Additional OAuth 2.0 and IMS Information](#additional-oauth-20-and-ims-information)
    - [Free trial users (JWT authentication)](#free-trial-users-jwt-authentication)
  - [Automating your JWT token](#automating-your-jwt-token)
      - [Additional Service Token and JWT Information](#additional-service-token-and-jwt-information)
  - [API Keys](#api-keys)
  - [Retries](#retries)
  - [Rate Limiting](#rate-limiting)
  - [Quota Limits](#quota-limits)
- [Photoshop](#photoshop)
  - [General Workflow](#general-workflow)
    - [Input and Output file storage](#input-and-output-file-storage)
    - [Tracking document changes](#tracking-document-changes)
  - [Supported Features](#supported-features)
    - [SmartObject](#smartobject)
    - [Text layers (`New!`)](#text-layers-new)
      - [Font handling](#font-handling)
      - [Handle missing fonts in the document.](#handle-missing-fonts-in-the-document)
      - [Limitations](#limitations)
    - [Photoshop Actions](#photoshop-actions)
      - [Execute Photoshop Actions (`New!`)](#execute-photoshop-actions-new)
      - [Usage Recommendations](#usage-recommendations)
      - [Known Limitations](#known-limitations)
    - [Rendering / Conversions](#rendering--conversions)
    - [Layer level edits](#layer-level-edits)
      - [The add, edit and delete objects](#the-add-edit-and-delete-objects)
    - [Document level edits](#document-level-edits)
    - [Artboards](#artboards)
    - [Compatibility with Photoshop versions](#compatibility-with-photoshop-versions)
  - [How to use the APIs](#how-to-use-the-apis)
    - [Example 1: /smartObject (Replacing smartobject)](#example-1-smartobject-replacing-smartobject)
      - [Sample 1: Replacing a SmartObject](#sample-1-replacing-a-smartobject)
      - [Sample 2: Creating a SmartObject](#sample-2-creating-a-smartobject)
    - [Example 2: Using /documentOperations to edit TextLayer(s)](#example-2-using-documentoperations-to-edit-textlayers)
      - [Sample 2.1: Making a text layer edit](#sample-21-making-a-text-layer-edit)
      - [Sample 2.2: Using a custom font in a text layer](#sample-22-using-a-custom-font-in-a-text-layer)
      - [Sample 2.3: Dictating actions for missing fonts](#sample-23-dictating-actions-for-missing-fonts)
    - [Example 3: /documentOperations (Making PSD edits and renders)](#example-3-documentoperations-making-psd-edits-and-renders)
      - [Sample 3.1: Making a simple edit](#sample-31-making-a-simple-edit)
      - [Sample 3.2: Creating new Renditions](#sample-32-creating-new-renditions)
      - [Sample 3.3: Swapping the image in a smart object layer](#sample-33-swapping-the-image-in-a-smart-object-layer)
      - [Sample 3.4: Adding a new adjustment layer](#sample-34-adding-a-new-adjustment-layer)
      - [Sample 3.5: Editing the image in a pixel layer](#sample-35-editing-the-image-in-a-pixel-layer)
    - [Example 4: /renditionCreate (Generating New Renditions)](#example-4-renditioncreate-generating-new-renditions)
      - [Sample 4.1: A single file input](#sample-41-a-single-file-input)
    - [Example 5: /documentManifest (Retrieving a PSD manifest)](#example-5-documentmanifest-retrieving-a-psd-manifest)
      - [Sample 5.1: Initiate a job to retrieve a PSD's JSON manifest](#sample-51-initiate-a-job-to-retrieve-a-psds-json-manifest)
    - [Example 6: Fetch the status of the job after successfully submitting a request](#example-6-fetch-the-status-of-the-job-after-successfully-submitting-a-request)
      - [Sample 6.1 Poll for job status and get the returned manifest (for the /documentManifest API)](#sample-61-poll-for-job-status-and-get-the-returned-manifest-for-the-documentmanifest-api)
      - [Sample 6.2 Poll for job status and get the results of all other APIs](#sample-62-poll-for-job-status-and-get-the-results-of-all-other-apis)
    - [Example 7: Execute Photoshop Actions](#example-7-execute-photoshop-actions)
      - [Sample 7.1 - Play ALL actions in .atn file.](#sample-71---play-all-actions-in-atn-file)
      - [Sample 7.2 - Play a specific action in an .atn file using `actionName`](#sample-72---play-a-specific-action-in-an-atn-file-using-actionname)
  - [Sample Code](#sample-code)
  - [Current Limitations](#current-limitations)
- [ImageCutout](#imagecutout)
  - [General Workflow](#general-workflow-1)
  - [How to use the API's](#how-to-use-the-apis)
    - [Example 1: Initiate a job to create an image cutout](#example-1-initiate-a-job-to-create-an-image-cutout)
    - [Example 2: Initiate a job to create an image mask](#example-2-initiate-a-job-to-create-an-image-mask)
  - [Customized Workflow](#customized-workflow)
    - [Example 3: (Generate ImageCutOut result as Photoshop path)](#example-3-generate-imagecutout-result-as-photoshop-path)
      - [Sample Input/Output](#sample-inputoutput)
      - [Instructions](#instructions)
      - [Sample Code](#sample-code-1)
- [Lightroom APIs](#lightroom-apis)
  - [General Workflow](#general-workflow-2)
  - [How to use the API's](#how-to-use-the-apis-1)
- [Using Webhooks through Adobe I/O Events](#using-webhooks-through-adobe-io-events)
  - [Registering your application to our Event Provider](#registering-your-application-to-our-event-provider)
    - [Prerequisites needed to use the Event Provider](#prerequisites-needed-to-use-the-event-provider)
    - [Registering the Webhook](#registering-the-webhook)
  - [Triggering an Event from the API's](#triggering-an-event-from-the-apis)
    - [Example 1: /documentManifest (Retrieving a PSD manifest from the Photoshop API)](#example-1-documentmanifest-retrieving-a-psd-manifest-from-the-photoshop-api)
      - [Step 1: Initiate a job to retrieve a PSD's JSON manifest](#step-1-initiate-a-job-to-retrieve-a-psds-json-manifest)
      - [Step 2: Receive the Job's status on the Webhook application when the job is complete](#step-2-receive-the-jobs-status-on-the-webhook-application-when-the-job-is-complete)
    - [Example 2: /autoTone (Auto tone an image through the Lightroom API)](#example-2-autotone-auto-tone-an-image-through-the-lightroom-api)
      - [Step 1: Initiate a job to auto tone an image](#step-1-initiate-a-job-to-auto-tone-an-image)
      - [Step 2: Receive the Job's status on the Webhook application when the job is complete](#step-2-receive-the-jobs-status-on-the-webhook-application-when-the-job-is-complete-1)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Public Beta

The Photoshop APIs are open for free trials. The trial is currently limited to 5,000 calls in a non production environment. In order to gain access to the trial please sign up using the link below and follow the steps to generate your trial credentials. https://photoshop.adobelanding.com/api-signup/

Make sure to take a look at the Pre-release agreement linked in the sign up form before getting started and ensure you understand the aspects of the program.


# Welcome to Photoshop APIs!

The Adobe Photoshop API gives you access to a subset of Photoshop, Lightroom, and Sensei  services. The API will allow you to make both layer and document level edits to Photoshop PSD files as well as perform a number of image edits and improvements.

The Photoshop API is designed with REST like principles and uses standard HTTP response codes, verbs and authentication and returns JSON-encoded responses.

The links below provide more detailed information about the API services including code samples and reference guides.  Once you are done setting up your Authentication you can dive into these links.

The API documentation is published at

[Photoshop API Reference](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop)

[Lightroom Getting Started](#lightroom-apis)

[Lightroom API Reference](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Lightroom)

[Image Cutout Getting Started](#imagecutout)

[Image Cutout API Reference](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei)

# General Setup and Onboarding

## Authentication
### Overview

The Photoshop API uses client id’s (also known as api keys) and authentication tokens to authenticate requests. There are two different kinds of authorization tokens available:
Internal Adobe user access (OAuth 2.0 access token)
Free trial user (Service token using JSON Web Token/JWT)
In order to use the Photoshop API's you’ll need to get an API key (also known as a CLIENT ID) and a Client Secret. Once you have those you can use them to programmatically get an access token to authenticate your requests. We’ll walk you through the steps below.


### Internal Adobe Users Only
1. Get your client id and client secret from the CIS team.
2. Test out your credentials.
  - Browse to https://ps-prerelease-us-east-1.cloud.adobe.io
  - Enter the client id and secret
  - Follow through the login process
  - If your credentials work you should see an authorization token appear on your screen
3. Make an authenticated call to ensure you can round trip successfully with the API’s
```shell
curl --request GET \
  --url https://image.adobe.io/pie/psdService/hello  \
  --header "Authorization: Bearer <YOUR_OAUTH_TOKEN>" \
  --header "x-api-key: <YOUR_CLIENT_ID>" \
```
  Congrats! You just made your first request to the Photoshop API.

4.  Make a Photoshop API call with real assets

  Now that you can successfully authenticate and talk to the API’s it’s time to make “real” calls…

  ```shell
  curl -X POST \
    https://image.adobe.io/pie/psdService/documentManifest \
    -H 'Authorization: Bearer <auth_token>' \
    -H 'Content-Type: application/json' \
    -H 'x-api-key: <YOUR_API_KEY>' \
    -d '{
    "inputs": [
      {
        "href":"files/Example.psd",
        "storage":"adobe"
      }
    ]
  }'
  ```

5.  Notes on token retrieval
The access token must never be transmitted as a URI parameter. Doing so would expose it to being captured in-the-clear by intermediaries such as proxy server logs. The API does not allow you to send an access token anywhere except the Authorization header field.

Your access token will expire typically in 24 hours. You will receive a ‘refresh_token’ when you initially obtain the access token that you can use to get a new access token. Be aware that refreshing your token might require a new login event. Please reference the OAuth documentation for additional instructions.
Please contact psdservices@adobe.com for more information on how you can automate token generation for your workflow.

#### Additional OAuth 2.0 and IMS Information

You can find details on interacting with Adobe IMS API’s and authentication in general
1. [General Authentication Information](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/AuthenticationGuide.md)
2. [OAuth Authentication](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/OAuth/OAuth.md)
3. [IMS API’s](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/Resources/IMS.md)
4. [OAuth Sample Code](sample_code/oauth-sample-app)

### Free trial users (JWT authentication)

NOTE: Free Trial users will not have access to assets stored in the Creative Cloud so you must use an external storage source when making calls to the API. All free trial users will have 5,000 API calls to test their use case and provide feedback. Please see [Quota Limits](#quota-limits) for more information.

1. If you haven't signed up and generated credentials please follow this link and follow the steps on the confirmation modal:
https://photoshop.adobelanding.com/api-signup/
2. If you have already signed up and need a new keyGo to https://console.adobe.io/home and sign in to the Admin Console.
3. Click on “Create a new project” under the “Quick Start” section on the middle of your screen
4. Click on “Add API”
5. Select the “Adobe Photoshop APIs (Trial)” and click on “Next”
6. You should see a zip file named “Config” in your downloads
7. Open the contents of the zip and locate the file name “private.key”
8. Open the file named “private.key” in a text editor like Atom or Sublime
9. Copy the entire contents of the file and paste it in your project page in the section labeled “Generate access token” and click on “Generate token” on the bottom right hand corner.
10. Congrats! You have just created a JWT token. Now copy your token and Client ID from this screen into a secure document. You are going to need them for the next step.
11. Open your terminal and paste the code below. Make sure to replace the variables "YOUR_ACCESS_TOKEN" and "YOUR_CLIENT_ID" with the information you copied from the last step and run the command.

``` shell

curl --request GET \
  --url https://image.adobe.io/pie/psdService/hello \
  --header "Authorization: Bearer <YOUR_ACCESS_TOKEN>" \
  --header "x-api-key: <YOUR_CLIENT_ID>"
  ```

Congrats! You just made your first request to the Photoshop API.

NOTE: Your token will expire every 24 hours and will need to be refreshed after it expires. See the next section for more information on retrieving your token programmatically.

## Automating your JWT token

Check out these modules for a quick path to automating your token retrieval:

- [JWT Instructions for Python](https://www.datanalyst.info/python/adobe-io-user-management/adobe-io-jwt-authentication-with-python/)
- [JWT Instructions for Node](https://www.npmjs.com/package/@adobe/jwt-auth)

#### Additional Service Token and JWT Information

You can find details on interacting with Adobe IMS API’s and authentication in general
  1. [General Authentication Information](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/AuthenticationGuide.md)
  2. [JWT/Service Token Authentication](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md)
  3. [IMS API’s](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/Resources/IMS.md)
  4. [JWT Sample Code](sample_code/jwt-sample-app)  

## API Keys

Also known as the `client_id`. You must additionally pass in your Adobe API key in the `x-api-key` header field. You’ll automatically get a developer API key when you create your Adobe I/O Console Integration.  After you've created your integration you can find your API key in the `Overview` tab of your Integration

## Retries

- The service will retry status codes of 429, 502, 503, 504 three times.
- You should only retry requests that have a 5xx response code. A 5xx error response indicates there was a problem processing the request on the server.
- You should implement an exponential back-off retry strategy with 3 retry attempts.
- You should not retry requests for any other response code.

## Rate Limiting

We have not put a throttle limit on requests to the API at this time.

## Quota Limits

All free trial users will have 5,000 API calls in order to test and evaluate the API in a non production environment. If for any reason you reach your limit and need to extend your quota please reach out psdservices@adobe.com for more information.


# Photoshop

## General Workflow

The typical workflow involves making one or more calls to `/documentOperations`, `/smartObject` to optionally edit an input PSD, and/or create new image renditions. Both endpoints are asynchronous so the response will contain the `/status` endpoint to poll for job status and results.

Optionally, another call can be made to retrieve the manifest file (a JSON representation of the documents layer tree) for this PSD document via the `/documentManifest` API.

### Input and Output file storage

Clients can use assets stored on one of the following storage types:
1. Adobe: by referencing the path to the files on Creative Cloud
2. External: (like AWS S3) by using a presigned GET/PUT URL
3. Azure: By generating a SAS (Shared Access Signature) for upload/download
4. Dropbox: Generate temporary upload/download links using https://dropbox.github.io/dropbox-api-v2-explorer/

### Tracking document changes

If you are making multiple edits to a PSD during the course of a user session it is your decision on how you want to track and store changes from one version of a PSD to another. Some clients will choose to refresh the document's JSON manifest by calling `/documentManifest` again after each call to `/documentOperations`. Other clients may choose to cache the changes locally and then make one final call to `/documentOperations` with the original PSD and the accumulated changes requested by the user.

## Supported Features

This is a partial list of currently supported features.  Please also see the [Release Notes](https://forums.adobeprerelease.com/photoshopapiservice/categories/releasenotes) for a list of added features

### SmartObject

The Photoshop APIs currently support creating and editing of Embedded Smart Objects. Support for Linked Smart Objects is forthcoming.

- In order to update an embedded smart object that is referenced by multiple layers you need to update each of those layers, then only the effect will be reflected in all layers referencing the same smart object.

- The replaced smart object is placed within the bounding box of the original image. If the new image is bigger or smaller than the original image, it fits into the original bounding box maintaining the aspect ratio. You can change the bounds of the replaced image by passing bounds parameters in the API call.

- If your document contains transparent pixels (e.g some .png) for the smart object layer, you may not get consistent bounds.

The API's are documented [here](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop-document_operations)

We also have an example of replacing a Smart Object within a layer.

[Smart Object Example Code](#sample-1-replacing-a-smartobject)

For better performance, we rasterize our smart objects that are bigger than  2000 pixels * 2000 pixels.

For optimal processing, please make sure the embedded smart object that you want to replace only contains alphanumeric characters in it's name.

### Text layers (`New!`)

The Photoshop APIs currently support creating and editing of Text Layer with different fonts, character styles and paragraph styles. The set of text attributes that can be edited is listed below:
- Edit the text contents
- Change the font (See the `Fonts` section for more info)
- Edit the font size
- Change the font color in the following formats: rgb, cmyk, gray, lab
- Edit the text orientation (horizontal/vertical)
- Edit the paragraph alignment (left, center, right, justify, justifyLeft, justifyCenter, justifyRight)

The API's are documented [here](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop-document_operations)

We also have an example of making a simple text layer edit.

[Text layer Example Code](#sample-21-making-a-text-layer-edit)

#### Font handling
In order to be able to correctly operate on text layers in the PSD, the corresponding fonts needed for these layers will need to be available when the server is processing the PSD. These include fonts from the following cases:
1. The font that is in the text layer being edited, but the font itself is not being changed
2. If the font in a text layer is being changed to a new font

While referencing fonts in the API request, please ensure that the correct Postscript name for that font is used. Referencing to that font with any other name will result in the API treating this as a missing font.

The Photoshop APIs supports using the following category of fonts:
- Currently Installed Fonts on the server listed [here](SupportedFonts.md)
- Fonts that you are authorized to access via [Adobe Fonts](https://fonts.adobe.com/fonts).
  **Note:** Currently only available for OAuth tokens, JWT service token support is forthcoming.
- Custom/Other Fonts: These are the fonts that are either owned by you or the ones that only you are authorized to use.
  To use a custom font you must include an href to the font in your request. Look at the `options.fonts` section of the API docs for more information.
  For including an href to the font in your request, please ensure the font file name to be in this format: `<font_postscript_name>.<ext>`, when it is being uploaded in your choice of storage. A sample `options.fonts` section will look like so:
  ```json
  {
    "storage": "adobe",
    "href": "/files/OpenSansCondensed-Light.ttf"
  }
  ```
  **Note:** This also applies to any other font present in the document which is not to be found in the first 2 categories above.

Here is an example usage of a custom font
[Custom font](#sample-22-using-a-custom-font-in-a-text-layer)

#### Handle missing fonts in the document.

The API provides two options to control the behavior when there are missing fonts, as the request is being processed:
- Specify a global font which would act as a default font for the current request: The `globalFont` field in the `options` section of the request can be used to specify the full postscript name of this font.
For any textLayer edit/add operation, if the font used specifically for that layer is missing, this font will be used as the default. If the global font itself is missing, then the action to be taken will be dictated by the `manageMissingFonts` options as explained here in the next bullet point.

  **Note**: If using an OAuth integration, Adobe Fonts can be used as a global font as well. If the global font is a custom font, please upload the font to one of the cloud storage types that is supported and specify the `href` and `storage` type in the `options.fonts` section of the request.
- Specify the action to be taken if one or more fonts required for the add/edit operation(s) are missing: The `manageMissingFonts` field in the `options` section of the request can be used to specify this action. It can accept one of the following 2 values:
  - `fail` to force the request/job to fail
  - `useDefault` to use our system designated default font, which is: `ArialMT`

Here is an example usage of `manageMissingFonts` and `globalFont`
[Handle missing fonts](#sample-23-dictating-actions-for-missing-fonts)

#### Limitations
- Most of the text attributes retain their respective original values. There are some attributes however that do not retain their original values. For example (and not limited to): tracking, leading, kerning

### Photoshop Actions
#### Execute Photoshop Actions (`New!`)

Adobe Photoshop APIs supports playing back Photoshop Actions recorded from Photoshop.  <a href="https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop-photoshopActions" target="_blank">Click here to see API documentation</a>

An action is a series of tasks that you play back on a single file or a batch of files—menu commands, panel options, tool actions, and so on. For example, you can create an action that changes the size of an image, applies an effect to the image, and then saves the file in the desired format.

For more information on how to create Photoshop Actions, see <a href="https://helpx.adobe.com/photoshop/using/actions-actions-panel.html" target="_blank">Adobe Help Center</a>

#### Usage Recommendations
* Create actions that do not open any operating system dialogs. All Photoshop dialogs are supported, but not operating system dialogs.
* It is recommended to create Actions that do not require user interactions.
* Input and Output file format should be any of PSD, JPEG, PNG, or TIFF.
* Make sure to test your actions on Photoshop, with several different input/images. If it has any errors on Photoshop, it won't run successfully on our servers either.

#### Known Limitations
The following are known limitations for the Alpha release

* Not supported, 3D and Video features
* Custom presets (for example color swatches and brushes)

Here are examples of submitting and executing Photoshop Actions.
[Execute Photoshop Actions](#sample-71---play-all-actions-in-atn-file)

### Rendering / Conversions

- Create a new PSD document
- Create a JPEG, TIFF or PNG rendition of various sizes
- Request thumbnail previews of all renderable layers
- Convert between any of the supported filetypes (PSD, JPEG, TIFF, PNG)

Here is an example of creating JPEG and PNG rendtions of a PSD document.
[Render PSD document](#sample-41-a-single-file-input)

### Layer level edits

- General layer edits
  - Edit the layer name
  - Toggle the layer locked state
  - Toggle layer visibility
  - Move or resize the layer via it's bounds
  - Delete layers
- Adjustment layers
  - Add or edit an adjustment layer. The following types of adjustment layers are currently supported:
  - Brightness and Contrast
  - Exposure
  - Hue and Saturation
  - Color Balance
- Image/Pixel layers
  - Add a new pixel layer, with optional image
  - Swap the image in an existing pixel layer
- Shape layers
  - Resize a shape layer via it's bounds

#### The add, edit and delete objects

The `/documentOperations` API should primarily be used to make layer and/or document level edits to your PSD and then generate new renditions with the changes. You can pass in a flat array of only the layers that you wish to act upon, in the `options.layers` argument of the request body.
The layer name (or the layer id) will be used by the service to identify the correct layer to operation upon in your PSD.

The `add`, `edit`, `move` and `delete` blocks indicate the action you would like to be taken on a particular layer object. Any layer block passed into the API that is missing one of these attributes will be ignored.
The `add` and `move` blocks must also supply one of the attributes `insertAbove`, `insertBelow`, `insertInto`, `insertTop` or `insertBottom` to indicate where you want to move the layer to. More details on this can be found in the API documentation.

**Note**: Adding a new layer does not require the ID to be included, the service will generate a new layer id for you.

Here are some examples of making various layer level edits.
- [Layer level editing](#sample-31-making-a-simple-edit)
- [Adding a new Adjustment Layer](#sample-34-adding-a-new-adjustment-layer)
- [Editing Image in a Pixel Layer](#sample-35-editing-the-image-in-a-pixel-layer)

### Document level edits

- Crop a PSD
- Resize a PSD

### Artboards

- Show artboard information in the JSON Manifest
- Create a new artboard from multiple input psd's

### Compatibility with Photoshop versions

1. The API’s will open any PSD created with Photoshop 1.0 through the current release and this will always be true.
2.  When saving as PSD, the API’s will create PSD’s compatible with the current shipping Photoshop.
3.  In regards to “maximize compatibility” referenced in [https://helpx.adobe.com/photoshop/using/file-formats.html#maximize_compatibility_for_psd_and_psb_files](https://helpx.adobe.com/photoshop/using/file-formats.html#maximize_compatibility_for_psd_and_psb_files)  the API's default to “yes”

## How to use the APIs

The API's are documented at https://adobedocs.github.io/photoshop-api-docs-pre-release/

### Example 1: /smartObject (Replacing smartobject)

The `/smartObject` endpoint can take an input PSD file with an embedded smartobject and can replace with another smartobject.
This API is a simple API developed to ease the smartObject replacement workflow for an user.

#### Sample 1: Replacing a SmartObject
This example shows how you can replace an embedded smart object

``` shell
curl - H "Authorization: Bearer $token" \
- H "x-api-key: $api_key" \
- X POST \
https: //image.adobe.io/pie/psdService/smartObject \
- d '{
  "inputs": [
  {
    "href": "files/SOCreate.psd",
    "storage": "adobe"
  }],
  "options": {
    "layers": [{
      "name": "New",
      "input": {
        "href": "files/jt-guitar.jpeg",
        "storage": "adobe"
      }
     }
    ]
  },
  "outputs": [
  {
    "storage": "adobe",
    "href": "files/SOedit.psd",
    "type": "vnd.adobe.photoshop"
  }
]}'
```

#### Sample 2: Creating a SmartObject
This example shows how you can create an embedded smart object

``` shell
curl - H "Authorization: Bearer $token" \
- H "x-api-key: $api_key" \
- X POST \
https: //image.adobe.io/pie/psdService/smartObject
- d '{
  "inputs": [
  {
    "href": "files/SO.psd",
    "storage": "adobe"
  }],
  "options": {
    "layers": [{
      "name": "New",
      "add": {
        "insertTop": true
      },
      "input": {
        "href": "files/jt-drums.jpeg",
        "storage": "adobe"
       }
      }
    ]
  },
  "outputs": [
  {
    "storage": "adobe",
    "href": "files/SOCreate.psd",
    "type": "vnd.adobe.photoshop"
  }
]}'
```

A call to this API initiates an asynchronous job and returns a response containing an href. Use the value in the href to poll for the status of the job. This is illustrated in [Example 6](#example-6-fetch-the-status-of-the-job-after-successfully-submitting-a-request).

### Example 2: Using /documentOperations to edit TextLayer(s)

This example section will provide information and samples to demonstrate the use of `/documentOperations` API to work with Text Layers in particular.
Please refer to the [The add, edit and delete objects](#the-add-edit-and-delete-objects) section for more information on how to apply these operations on a text layer.

#### Sample 2.1: Making a text layer edit

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H "Authorization: Bearer $token"  \
  -H "x-api-key: $apiKey" \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "name": "My Text Layer",
        "type": "textLayer",
        "text": {
            "content": "CHANGED TO NEW TEXT",
            "characterStyles": [{
                "fontSize": 15,
                "orientation": "horizontal",
                "fontColor": {
                    "rgb":{
                       "red":26086,
                       "green":23002,
                       "blue":8224
                    }
                }
            }],
            "paragraphStyles": [{
              "alignment": "right"
            }]
        },
        "edit": {}
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}'
```

#### Sample 2.2: Using a custom font in a text layer
This will change the font in a text layer named `My Text Layer` to a custom font `VeganStylePersonalUse`.
**Note**: the value for the `fontName` field in the `text.characterStyles` section is the full postscript name of the custom font.

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H "Authorization: Bearer $token"  \
  -H "x-api-key: $apiKey" \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "fonts": {
        storage: "adobe",
        href: "files/pits/input/VeganStylePersonalUse.ttf"
    },
    "layers":[
      {
        "name": "My Text Layer",
        "type": "textLayer",
        "text": {
            "content": "CHANGED TO NEW TEXT WITH NEW FONT",
            "characterStyles": [{
                "fontName": "VeganStylePersonalUse",
                "orientation": "horizontal",
                "fontColor": {
                    "rgb":{
                       "red":26086,
                       "green":23002,
                       "blue":8224
                    }
                }
            }]
        },
        "edit": {}
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}'
```

#### Sample 2.3: Dictating actions for missing fonts
In this request for example, if `MySampleFont` is not found while processing the request, the system default font (`ArialMT`) will be used as `manageMissingFonts` is set to `useDefault`
```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H "Authorization: Bearer $token"  \
  -H "x-api-key: $apiKey" \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "manageMissingFonts": "useDefault",
    "globalFont": "MySampleFont",
    "fonts": {
        storage: "adobe",
        href: "files/pits/input/VeganStylePersonalUse.ttf"
    },
    "layers":[
      {
        "name": "My Text Layer",
        "type": "textLayer",
        "text": {
            "content": "CHANGED TO NEW TEXT WITH NEW FONT",
            "characterStyles": [{
                "fontName": "VeganStylePersonalUse",
                "orientation": "horizontal",
                "fontColor": {
                    "rgb":{
                       "red":26086,
                       "green":23002,
                       "blue":8224
                    }
                }
            }]
        },
        "edit": {}
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}'
```

A call to this API initiates an asynchronous job and returns a response containing an href. Use the value in the href to poll for the status of the job. This is illustrated in [Example 6](#example-6-fetch-the-status-of-the-job-after-successfully-submitting-a-request).

### Example 3: /documentOperations (Making PSD edits and renders)

The `/documentOperations` API can be used to make layer and/or document level edits to your PSD and then generate new renditions with the changes. You can pass in a flat array of only the layers that you wish to act upon, in the request body's `options.layers` argument.

The layer name (or the layer id) will be used by the service to identify the correct layer to operation upon in your PSD.
Please refer to the [The add, edit and delete objects](#the-add-edit-and-delete-objects) section for more information on how to apply these operations on a layer.

#### Sample 3.1: Making a simple edit
```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H "Authorization: Bearer $token"  \
  -H "x-api-key: $apiKey" \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "edit":{},     
        "id":750,
        "index":1,
        "locked":true,
        "name":"HeroImage",
        "type":"smartObject",
        "visible":true
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}'
```

#### Sample 3.2: Creating new Renditions

See the `/renditionCreate` examples below as the format for the `outputs` object in the request body is identical

#### Sample 3.3: Swapping the image in a smart object layer

In this example we want to swap the smart object in an existing embedded smart object layer, the Hero Image layer in Example.psd. We are requesting the following:

- The `edit` key is included to indicate we want to edit this layer
- The `layers.input` object is included to indicate where the replacement image can be found
- The `layers.smartObject` object is included to indicate specific information related to this image as SO

All the files used in the example are available in [sample_files](master/sample_files). You can download the files and put it in your CC account or any storage(AWS, Azure or Dropbox).

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H "Authorization: Bearer $token"  \
  -H "x-api-key: $apiKey" \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "edit":{},     
        "input":{                                       
          "href":"files/heroImage.png",  
          "storage":"adobe"
        },
        "smartObject" : {                
          "type" : "image/png"
        },
        "attributes":{
          "bounds":{
            "height":515,
            "left":-385,
            "top":-21,
            "width":929
          }
        },
        "id":750,
        "index":1,
        "locked":false,
        "name":"HeroImage",
        "type":"smartObject",
        "visible":true
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}'
```

A call to this API initiates an asynchronous job and returns a response containing an href. Use the value in the href to poll for the status of the job. This is illustrated in [Example 6](#example-6-fetch-the-status-of-the-job-after-successfully-submitting-a-request).

#### Sample 3.4: Adding a new adjustment layer

This example shows how you can add a new brightnessContrast adjustment layer to the top of your PSD.  Things to note:

- NEW KEYWORD TO INDICATE AN ADDITION: The `add` key is included, along with `insertAbove` in the new layer object to indicate exactly where you want the new layer placed in the overall Manifest tree.  
- LAYER TYPE IS REQUIRED: The type indicates you want a new layer of type adjustment layer.
- LAYER ID AND INDEX ARE NOT PRESENT: The layer index and id are not supported for add operations. The index is implied by the objects position in the manifest tree and the ID will be generated by the service and returned to you in subsequent calls to `/documentManifest`

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {                                        
        "add":{                               // <--- NEW KEYWORD TO INDICATE AN ADDITION
          "insertAbove": {
            "id": 549
          }                     // <--- INDICATES THE LAYER SHOULD BE CREATED ABOVE ID 549
        },
        "adjustments":{
          "brightnessContrast":{
            "brightness":25,
            "contrast":-40
          }
        },
        "name":"NewBrightnessContrast",
        "type":"adjustmentLayer"              // <--- LAYER TYPE IS REQUIRED
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.jpeg",
      "storage":"adobe",
      "type":"image/jpeg"
    }
  ]
}'
```

A call to this API initiates an asynchronous job and returns a response containing an href. Use the value in the href to poll for the status of the job. This is illustrated in [Example 6](#example-6-fetch-the-status-of-the-job-after-successfully-submitting-a-request).

#### Sample 3.5: Editing the image in a pixel layer

In this example we want to replace the image in an existing pixel layer, the Hero Image layer in Example.psd. We are requesting the following:

- NEW KEYWORD TO INDICATE AN EDIT: The `edit` key is included to indicate we want to edit this layer
- NEW KEYWORD TO INDICATE IMAGE REPLACEMENT INFO: The `layers.input` object is included to indicate where the replacement image can be found

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentOperations \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "options":{
    "layers":[
      {
        "edit":{},                    // <--- NEW KEYWORD TO INDICATE AN ADDITION
        "input":{                                       // <--- NEW KEYWORD TO INDICATE IMAGE REPLACEMENT INFO
          "href":"/files/newBackgroundImage.jpeg",
          "storage":"adobe"
        },
        "bounds":{
          "height":405,
          "left":0,
          "top":237,
          "width":300
        },
        "id":751,
        "index":2,
        "locked":false,
        "name":"BackgroundGradient",
        "type":"layer",
        "visible":true
      }
    ]
  },
  "outputs":[
    {
      "href":"files/Example_Out.psd",
      "storage":"adobe",
      "type":"vnd.adobe.photoshop",
      "overwrite":true
    }
  ]
}
'
```

A call to this API initiates an asynchronous job and returns a response containing an href. Use the value in the href to poll for the status of the job. This is illustrated in [Example 6](#example-6-fetch-the-status-of-the-job-after-successfully-submitting-a-request).

### Example 4: /renditionCreate (Generating New Renditions)

The `/renditionsCreate` endpoint can take a number of input PSD files and generate new image renditions or a new PSD

#### Sample 4.1: A single file input

This sample API call will request two different output renditions from our Example.psd input:

- `Example.jpeg` is a new JPEG rendition that has a width of 512 pixels
- `Example.png` is a new fullsize PNG rendition

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/renditionCreate \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs":[
    {
      "href":"files/Example.psd",
      "storage":"adobe"
    }
  ],
  "outputs":[
    {
      "href":"files/Example.jpeg",          
      "width": 512,
      "storage":"adobe",
      "type":"image/jpeg"      
    },
    {
      "href":"files/Example.png",
      "storage":"adobe",
      "type":"image/png"
    }
  ]
}'
```

A call to this API initiates an asynchronous job and returns a response containing an href. Use the value in the href to poll for the status of the job. This is illustrated in [Example 6](#example-6-fetch-the-status-of-the-job-after-successfully-submitting-a-request).

### Example 5: /documentManifest (Retrieving a PSD manifest)

The `/documentManifest` api can take one or more input PSD's to generate JSON manifest files from. The JSON manifest is the tree representation of all of the layer objects contained in the PSD document.

#### Sample 5.1: Initiate a job to retrieve a PSD's JSON manifest

Using Example.psd, with the use case of a document stored in your external storage (ie. azure, aws, dropbox), a typical curl call might look like this:

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentManifest \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
  "inputs": [
    {
      "href":"<YOUR_PRESIGNED_URL>",
      "storage":"external"
    }
  ]
}'
```
A call to this API initiates an asynchronous job and returns a response containing an href. Use the value in the href to poll for the status of the job and the same response will also contain the JSON manifest. This is illustrated in [Example 6](#example-6-fetch-the-status-of-the-job-after-successfully-submitting-a-request) below.

###  Example 6: Fetch the status of the job after successfully submitting a request
Each of our Photoshop APIs, when invoked, initiates an asynchronous job and returns a response body that contains the href to poll for status of the job.

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/pie/psdService/status/de2415fb-82c6-47fc-b102-04ad651c5ed4"
        }
    }
}
```
Using the job id returned from the response (ass above) of a successfully submitted API call, you can poll on the corresponding value in the `href` field, to get the status of the job.

```shell
curl -X GET \
  https://image.adobe.io/pie/psdService/status/de2415fb-82c6-47fc-b102-04ad651c5ed4 \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```
#### Sample 6.1 Poll for job status and get the returned manifest (for the /documentManifest API)

Once your job completes successfully (no errors/failures reported), the status response will contain your document's JSON manifest along with other metadata about the input document. The JSON Manifest is further described in the [api docs](https://git.corp.adobe.com/pages/dice/pie-in-the-sky/#api-Documents-document_manifest_status)

```json
{
  "jobId":"63c6e812-6cb8-43de-8a60-3681a9ec6feb",
  "outputs":[
    {
      "input":"files/Example.psd",
      "status":"succeeded",
      "created":"2018-08-24T23:07:36.8Z",
      "modified":"2018-08-24T23:07:37.688Z",
      "layers":[
        {
          "bounds":{
            "height":64,
            "left":12,
            "top":1,
            "width":39
          },
          "id":549,
          "index":8,
          "locked":false,
          "name":"CompanyLogo",
          "type":"smartObject",
          "visible":true
        },
        {
          "bounds":{
            "height":153,
            "left":31,
            "top":334,
            "width":197
          },
          "children":[
            {
              "bounds":{
                "height":136,
                "left":29,
                "top":326,
                "width":252
              },
              "text": {
                "content":"Reset your customers’ expectations.",
                "paragraphStyles":[
                  {   
                    "alignment":"left"
                  }
                ],
                "characterStyles":[{
                  "fontAvailable":true,
                  "fontName":"AdobeClean-Bold",
                  "fontSize":36,
                  "orientation":"horizontal",
                }]               
              },
              "id":412,
              "index":6,
              "locked":false,
              "name":"Reset your customers’ expectations.",
              "type":"textLayer",
              "visible":true
            },
            {
              "bounds":{
                "height":67,
                "left":30,
                "top":452,
                "width":230
              },
              "text":{
                "content":"Get our retail experience article and infographic.",
                "paragraphStyles":[{
                  "alignment":"left"
                }],
                "characterStyles":[{
                  "fontAvailable":true,
                  "fontName":"AdobeClean-Regular",
                  "fontSize":15,
                  "orientation":"horizontal",
                }]
              },
              "id":676,
              "index":5,
              "locked":false,
              "name":"Get our retail experience article and infographic.",
              "type":"textLayer",
              "visible":true
            }
          ],
          "id":453,
          "index":7,
          "locked":false,
          "name":"Headline",
          "type":"layerSection",
          "visible":true
        },
        {
          "bounds":{
            "height":34,
            "left":31,
            "top":508,
            "width":99
          },
          "id":762,
          "index":3,
          "locked":false,
          "name":"CallToAction",
          "type":"smartObject",
          "visible":true
        },
        {
          "bounds":{
            "height":405,
            "left":0,
            "top":237,
            "width":300
          },
          "id":751,
          "index":2,
          "locked":false,
          "name":"BackgroundGradient",
          "type":"layer",
          "visible":true
        },
        {
          "bounds":{
            "height":515,
            "left":-385,
            "top":-21,
            "width":929
          },
          "id":750,
          "index":1,
          "locked":false,
          "name":"HeroImage",
          "type":"smartObject",
          "visible":true
        },
        {
          "bounds":{
            "height":600,
            "left":0,
            "top":0,
            "width":300
          },
          "id":557,
          "index":0,
          "locked":false,
          "name":"Background",
          "type":"layer",
          "visible":true
        }
      ],
      "document":{
        "height":600,
        "name":"Example.psd",
        "width":300
      }
    }
  ],
  "_links":{
    "self":{
      "href":"https://image.adobe.io/pie/psdService/status/8ec6e4f5-b580-41ac-b693-a72f150fec59"
    }
  }
}
```
#### Sample 6.2 Poll for job status and get the results of all other APIs

Once your job completes successfully (no errors/failures reported), this will return a response body containing the job status for each requested output. For the `/renditionCreate` API call in Example 4 in Sample 4.1 as illustrated above, a sample response containing the job status is as shown below:

```json
{
  "jobId":"de2415fb-82c6-47fc-b102-04ad651c5ed4",
  "outputs":[
    {
      "input":"/files/Example.psd",
      "status":"succeeded",
      "created":"2018-01-04T12:57:15.12345:Z",
      "modified":"2018-01-04T12:58:36.12345:Z",
      "_links":{
        "renditions":[
          {
            "href":"files/Example.jpeg",          
            "width": 512,
            "storage":"adobe",
            "type":"image/jpeg"    
          },
          {
            "href":"files/Example.png",
            "storage":"adobe",
            "type":"image/png"
          }
        ]
      }
    }
  ],
  "_links":{
    "self":{
      "href":"https://image.adobe.io/pie/psdService/status/de2415fb-82c6-47fc-b102-04ad651c5ed4"
    }
  }
}
```

###  Example 7: Execute Photoshop Actions

#### Sample 7.1 - Play ALL actions in .atn file.
```
export token=<YOUR_TOKEN>
export api_key =<YOUR_API_KEY>
curl -H "Authorization: Bearer $token" -H "x-api-key: $api_key" https://image.adobe.io/pie/psdService/photoshopActions -d '{
  "inputs": [
    {
      "href": "https://as2.ftcdn.net/jpg/02/49/48/49/500_F_249484911_JifPIzjUqzkRhcdMkF9GnsUI9zaqdAsn.jpg",
      "storage": "external"
    }
  ],
  "options": {
    "actions": [
      {
        "href": "https://raw.githubusercontent.com/johnleetran/ps-actions-samples/master/actions/Oil-paint.atn",
        "storage": "external"
      }
    ]
  },
  "outputs": [
    {
      "storage": "adobe",
      "type": "image/jpeg",
      "overwrite": true,
      "href": "files/ps-action-example/output.jpeg"
    }
  ]
}'
```
#### Sample 7.2 - Play a specific action in an .atn file using `actionName`

By default, Photoshop API will attempt to play all actions in an action set.  If you would like to only playback a specific action, you can specify `actionName` and the name of the action you want to invoke (see example below).

```
export token=<YOUR_TOKEN>
export api_key =<YOUR_API_KEY>
curl -H "Authorization: Bearer $token" -H "x-api-key: $api_key" https://image.adobe.io/pie/psdService/photoshopActions -d '{
  "inputs": [
    {
      "href": "https://as2.ftcdn.net/jpg/02/49/48/49/500_F_249484911_JifPIzjUqzkRhcdMkF9GnsUI9zaqdAsn.jpg",
      "storage": "external"
    }
  ],
  "options": {
    "actions": [
      {
        "href": "https://raw.githubusercontent.com/johnleetran/ps-actions-samples/master/actions/Oil-paint.atn",
        "storage": "external",
        "actionName": "Action 51"
      }
    ]
  },
  "outputs": [
    {
      "storage": "adobe",
      "type": "image/jpeg",
      "overwrite": true,
      "href": "files/ps-action-example/output.jpeg"
    }
  ]
}'
```

## Sample Code

The [sample_code](sample_code) folder in this repo contains sample code for calling the Photoshop APIs.

Note that the sample code is covered by the MIT license.


## Current Limitations
There are a few limitations to the APIs you should be aware of ahead of time.  
- Multi-part uploads and downloads are not yet supported
- The `/documentOperations` , `/documentManifest`, `/renditionCreate` and `/smartObject` endpoints only support a single PSD input
- Error handling is a work in progress. Sometimes you may not see the most helpful of messages

The file Example.psd is included in this repository if you'd like to experiment with these example calls on your own.
# ImageCutout


The Image Cutout API is powered by Sensei, Adobe’s Artificial Intelligence Technology, and Photoshop. The API's can identify the main subject of an image and produce two types of outputs. You can create a greyscale [mask](https://en.wikipedia.org/wiki/Layers_(digital_image_editing)#Layer_mask) png file that you can composite onto the original image (or any other).  You can also create a cutout where the mask has already composited onto your original image so that everything except the main subject has been removed.


| Original        | Mask           | Cutout  |
| :-------------: |:-------------:| :-----:|
| ![Alt text](assets/sensei_orig.jpg?raw=true "Original Image") | ![Alt text](assets/sensei_mask.png?raw=true "Mask") | ![Alt text](assets/sensei_cutout.png?raw=true "Original Image") |


## General Workflow

The typical workflow involves making an API POST call to the endpoint https://image.adobe.io/sensei for which the response will contain a link to check the status of the asynchronous job. Making a GET call to this link will return the status of the job and, eventually, the links to your generated output.

## How to use the API's

The API's are documented at [https://adobedocs.github.io/photoshop-api-docs/#api-Sensei](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei)

First be sure to follow the instructions in the [Authentication](#authentication) section to get your token.

### Example 1: Initiate a job to create an image cutout

The `/cutout` api takes a single input image to generate your mask or cutout from. Using Example.jpg, with the use case of a document stored in Adobe's Creative Cloud, a typical curl call might look like this:

```shell
curl -X POST \
  https://image.adobe.io/sensei/cutout \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{
   "input":{
      "storage":"adobe",
      "href":"/files/images/Example.jpg"
   },
   "output":{
      "storage":"adobe",
      "href":"/files/output/cutout.png",
      "mask":{
         "format":"binary"
      }
   }
}'
```

This initiates an asynchronous job and returns a response containing the href to poll for job status and the JSON manifest.
```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/sensei/status/e3a13d81-a462-4b71-9964-28b2ef34aca7"
        }
    }
}
```


Using the job id returned from the previous call you can poll on the returned `/status` href to get the job status

```shell
curl -X GET \
  https://image.adobe.io/sensei/status/e3a13d81-a462-4b71-9964-28b2ef34aca7 \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```

Once the job is complete your successful `/status` response will look similar to the response below; The output will have been placed in your requested location. In the event of failure the errors will be shown instead

```json
{
    "jobID": "e3a13d81-a462-4b71-9964-28b2ef34aca7",
    "status": "succeeded",
    "created": "2020-02-11T21:08:43.789Z",
    "modified": "2020-02-11T21:08:48.492Z",
    "input": "/files/images/Example.jpg",
    "_links": {
        "self": {
            "href": "https://image-stage.adobe.io/sensei/status/e3a13d81-a462-4b71-9964-28b2ef34aca7"
        }
    },
    "output": {
        "storage": "adobe",
        "href": "/files/output/cutout.png",
        "mask": {
            "format": "binary"
        }
    }
}
```

### Example 2: Initiate a job to create an image mask

The workflow is exactly the same as [creating an image cutout](#example-1-initiate-a-job-to-create-an-image-cutout) except you use the `/mask` endpoint instead of `/cutout`.  

## Customized Workflow
This section will demonstrate how to make a 'customized workflow' by chaining different APIs. 

### Example 3: (Generate ImageCutOut result as Photoshop path)
This workflow is ONLY for users who'd like to generate cutout result as Photoshop path (instead of regular mask or cutout in above example 1 and example 2). You will need to chain API calls to ImageCutOut service and Photoshop Service to achieve this goal. 

#### Sample Input/Output
Sample input from [here](assets/ic_customized_workflow/input.jpg)
Sample output from [here](assets/ic_customized_workflow/result_with_path.jpg) (Note: you will need to open result in Photoshop Desktop application so that you will see the path in path panel)

#### Instructions

1. Download the make-file.atn file from [here](assets/ic_customized_workflow/make-path.atn) (this file will be used in the Photoshop action API call)
2. Make the first API call one to ImageCutOut service to generate intermediate result as RGBA cutout (https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Sensei-cutout)
3. Make the second API call to Photoshop action service to use above intermediate result as well as the make-file.atn file to generate final JPEG format result with desired PS path embedded (https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Photoshop-photoshopActions)
4. Open the final result with Photoshop Desktop app to check generated path in path panel 


#### Sample Code
You can download the sample end-to-end bash script [here](sample_code/ic-customized-workflow-app) and then follow the comments to try it out this customized workflow. 



# Lightroom APIs

The Adobe Lightroom APIs allow you to make Lightroom-like automated edits to image files.

## General Workflow

The typical workflow involves making an API POST call to the endpoint https://image.adobe.io/lrService/ for which the response will contain a link to check the status of the asynchronous job. Making a GET call to this link will return the status of the job and, eventually, the links to your generated output.

## How to use the API's

The API's are documented at [https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Lightroom](https://adobedocs.github.io/photoshop-api-docs-pre-release/#api-Lightroom)

# Using Webhooks through Adobe I/O Events
Adobe I/O Events offers the possibility to build an event-driven application, based on events originating from Photoshop and Lightroom API's. To start listening for events, your application needs to register a webhook URL, specifying the Event Types to receive. Whenever a matching event gets triggered, your application is notified through an HTTP POST request to the webhook URL.
The Event Provider for Photoshop and Lightroom API's is `Imaging API Events`.
This event provider has two event types:
1. `Photoshop API events`
2. `Lightroom API events`

As the names indicate, these event types represent events triggered by the individual APIs.
## Registering your application to our Event Provider
### Prerequisites needed to use the Event Provider
1. Only supported for a `Service Integration`: You will have to create your own Service Integration, please refer to [this](#service-token-workflow-adobe-etla-users) section of the document for details on how to create a Service Integration.
2. Make sure that the integration is created under your own Organization Role in https://console.adobe.io and this will ensure that you have a unique `Organization ID`. A typical ID would look something like this: `ABCDEF123B6CCB7B0A495E2E@AdobeOrg` and can be found in the overview section of the details of the integration.
3. Create a Webhook application. [This](https://www.adobe.io/apis/experienceplatform/events/docs.html#!adobedocs/adobeio-events/master/intro/webhook_docs_intro.md#your-first-webhook) page gives all the details of what the skeleton of a basic application would look like. You can find a sample NodeJS application [here](sample_code/webhook-sample-app)

### Registering the Webhook
Once the above prerequisites are met, you can now proceed to register the webhook to the service integration. The steps to do that can be found  [here](https://www.adobe.io/apis/experienceplatform/events/docs.html#!adobedocs/adobeio-events/master/intro/webhook_docs_intro.md#registering-the-webhook).
After the webhook has been successfully registered, you will start to receive the events for any submitted job that either succeeded or failed, from the Event Types selected. This eliminates the need for your application to poll for the status of the job using the jobID.

## Triggering an Event from the API's
In order to start receiving the events in your Webhook Application, the additional thing that needs to be done is to pass in your IMS ORG ID in a header: `x-gw-ims-org-id: <YOUR_IMS_ORG_ID>`, when you make an API call to initiate a job. Please have a look at the examples below that demonstrates the usage of the new header and a sample event received for that job.
### Example 1: /documentManifest (Retrieving a PSD manifest from the Photoshop API)

#### Step 1: Initiate a job to retrieve a PSD's JSON manifest

The `/documentManifest` api can take one or more input PSD's to generate JSON manifest files from. The JSON manifest is the tree representation of all of the layer objects contained in the PSD document. Using Example.psd, with the use case of a document stored in Adobe's Creative Cloud, a typical curl call might look like this:

```shell
curl -X POST \
  https://image.adobe.io/pie/psdService/documentManifest \
  -H 'Authorization: Bearer <auth_token>' \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -H 'x-gw-ims-org-id: <YOUR_IMS_ORG_ID>' \
  -d '{
  "inputs": [
    {
      "href":"<SIGNED_GET_URL>",
      "storage":"external"
    }
  ]
}'
```

This initiates an asynchronous job and returns a response containing the href to poll for job status and the JSON manifest.
```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/pie/psdService/status/63c6e812-6cb8-43de-8a60-3681a9ec6feb"
        }
    }
}
```
#### Step 2: Receive the Job's status on the Webhook application when the job is complete
The value in the key `body` inside the event JSON contains the result of the job. Here is a sample event received from the job initiated above:
```json
{
  "event_id": "b412a90e-8bc0-4f0d-931e-9e9b8d24993d",
  "event": {
    "header": {
      "msgType": "JOB_COMPLETION_STATUS",
      "msgId": "8afa1a46-2733-406c-a646-e1c1acdee333",
      "imsOrgId": "<YOUR_IMS_ORG_ID>",
      "eventCode": "photoshop-job-status",
      "_pipelineMeta": {
        "pipelineMessageId": "1586288145511:631472:VA7_A1:142:0"
      },
      "_smarts": {
        "definitionId": "3ee6c9056a9d72fc40e09ddf5fdbb0af752e8e49",
        "runningSmartId": "psmart-yw6wosjksniuuathenny"
      },
      "_adobeio": {
        "imsOrgId": "<YOUR_IMS_ORG_ID>",
        "providerMetadata": "di_event_code",
        "eventCode": "photoshop-job-status"
      }
    },
    "body": {
      "jobId": "63c6e812-6cb8-43de-8a60-3681a9ec6feb",
      "outputs": [
        {
          "status": "succeeded",
          "layers": [
            {
              "id": 2,
              "index": 0,
              "type": "layer",
              "name": "Layer",
              "locked": false,
              "visible": true,
              "bounds": {
                "top": 0,
                "left": 0,
                "width": 100,
                "height": 100
              },
              "blendOptions": {
                "opacity": 100,
                "mode": "normal"
              }
            }
          ],
          "document": {
            "name": "test.psd",
            "width": 1000,
            "height": 1000,
            "bitDepth": 8,
            "imageMode": "rgb",
            "photoshopBuild": "Adobe Creative Imaging Service"
          }
        }
      ],
      "_links":{
        "self":{
          "href":"https://image.adobe.io/pie/psdService/status/8ec6e4f5-b580-41ac-b693-a72f150fec59"
        }
      }
    }
  }
}
```
### Example 2: /autoTone (Auto tone an image through the Lightroom API)

#### Step 1: Initiate a job to auto tone an image
```shell
curl -X POST \
  https://image.adobe.io/lrService/autoTone \
  -H "Authorization: Bearer $token" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <YOUR_API_KEY>" \
  -H 'x-gw-ims-org-id: <YOUR_IMS_ORG_ID>' \
  -d '{
    "inputs": {
      "href": "<SIGNED_GET_URL>",
      "storage": "external"
    },
    "outputs": [
    {
      "href": "<SIGNED_PUT_URL>",
      "type": "<type>",
      "storage": "external",
      "overwrite": <boolean>
    }
  ]
}'
```

This initiates an asynchronous job and returns a request body containing the href to poll for job status.

```json
{
    "_links": {
        "self": {
            "href": "https://image.adobe.io/lrService/status/eb4a9211-eb8a-4e88-b853-b9c08ba47427"
        }
    }
}
```
#### Step 2: Receive the Job's status on the Webhook application when the job is complete
The value in the key `body` inside the event JSON contains the result of the job. Here is a sample event received from the job initiated above:
```json
{
  "event_id": "7b59cc70-88d7-4895-b204-87f5350a0cce",
  "event": {
    "header": {
      "msgType": "JOB_COMPLETION_STATUS",
      "msgId": "eb4a9211-eb8a-4e88-b853-b9c08ba47427",
      "imsOrgId": "<YOUR_IMS_ORG_ID>",
      "eventCode": "lightroom-job-status",
      "_pipelineMeta": {
        "pipelineMessageId": "1586290300876:944289:VA7_A1:149:0"
      },
      "_smarts": {
        "definitionId": "3ee6c9056a9d72fc40e09ddf5fdbb0af752e8e49",
        "runningSmartId": "psmart-yw6wosjksniuuathenny"
      },
      "_adobeio": {
        "imsOrgId": "<YOUR_IMS_ORG_ID>",
        "providerMetadata": "di_event_code",
        "eventCode": "lightroom-job-status"
      }
    },
    "body": {
      "jobId": "eb4a9211-eb8a-4e88-b853-b9c08ba47427",
      "outputs": [
        {
          "input": "<SIGNED_GET_URL>",
          "status": "succeeded",
          "_links": {
            "self": [
              {
                "href": "<SIGNED_PUT_URL>",
                "storage": "external"
              }
            ]
          }
        }
      ],
      "_links": {
        "self": {
          "href": "https://image.adobe.io/lrService/status/eb4a9211-eb8a-4e88-b853-b9c08ba47427"
        }
      }
    }
  }
}
```
