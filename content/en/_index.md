---
title: "Samples Style Guide"
linkTitle: "Samples Style Guide"
type: docs
weight: 20
menu:
  main:
    weight: 20
---
 
## Introduction
 
This document serves as a definition of our samples standards for both
standalone snippets and sample applications. It is intended to help encourage
consistency and best practices when authoring code intended to teach others.
 
Even if not specifically mentioned in the guide, all samples should make
best-efforts to achieve the following goals wherever possible:
 
* **Copy-paste-runnable** - Users should be able to copy, paste, and run the
code into their environment with as few changes as possible. Samples should be
easy as possible for a user to run.
 
* **Teach through code** - Samples should teach users both how and _why_
specific best practices should be implemented and performed when interacting
with our services.
 
* **Idiomatic** - Samples should encourage idiomatic and best practices specific
to language, framework, or service.

## Structure

### Region tags
 
Each code snippet should have a region tag to define which parts of the snippet
are displayed from the documentation. Each region tag should be:
* Globally unique
* Consistent across the same snippets in different languages
* Begins with the product's region tag prefix
* In snake case

Region tags should show as much of the sample as possible, so that a user can
easily copy and pase the sample into their own environment to run it. 

### Imports
 
Samples should include any imports used in the sample.
 
This is easiest to enforce/detect when the samples are in their own file, so
samples should be structured as such unless their is a compelling reason not to.
 
{{< tabpane langEqualsHeader=true >}}
 {{< tab header="Java" >}}
   // Region tags should start after the package, but before imports.
   // [START product_example]
   import com.example.resource;
 
   public class exampleSnippet {
   // Snippet methods ...
   }
   // [END product_example]
 {{< /tab >}}
 {{< tab header="Python" >}}
  # [START product_example]
  import com.example.resource
 
  def example_snippet():
       # Snippet Content ...
 
  # [END product_example]
 {{< /tab >}}
{{< /tabpane >}}

### Sample description
 
Each code snippet file should have a top-level comment that succinctly describes
what the snippet does, including any setup (such as resources) required to make
the sample work:
 
{{< tabpane langEqualsHeader=true >}}
 {{< tab header="Java" >}}
   /**
   * Moves a persistent disk from one zone to another.
   *
   * See https://cloud.google.com/compute/docs/quickstart-client-libraries before running the code snippet.
   */
 {{< /tab >}}
{{< /tabpane >}}

### Arrange, Act, Assert

Generally, most samples should follow the "Arrange, Act, Assert" pattern as
closely as possible. Composing samples into these discrete steps can make them
more approachable to beginners:

1. **Arrange** - Create and configure the components for the request. Avoid
 nesting these components beyond 2-3 levels, as it can make parsing and
 understanding the samples more confusing.
1. **Act** - Send the request to the service and receive a response.
1. **Assert** - Verify that the call was successful and that a response was
 return as expected. This is typically done by printing some aspects of the
 response to stdout.

{{< tabpane langEqualsHeader=true >}}
 {{< tab header="Java" >}}
 // Lists the types of sensitive information the DLP API supports.
 public static void listInfoTypes() throws IOException {
   // Initialize client that will be used to send requests. This client only needs to be created
   // once, and can be reused for multiple requests. After completing all of your requests, call
   // the "close" method on the client to safely clean up any remaining background resources.
   try (DlpServiceClient dlpClient = DlpServiceClient.create()) {

     // Construct the request to be sent by the client
     ListInfoTypesRequest listInfoTypesRequest =
         ListInfoTypesRequest.newBuilder()
             // Only return infoTypes supported by certain parts of the API.
             // Supported filters are "supported_by=INSPECT" and "supported_by=RISK_ANALYSIS"
             // Defaults to "supported_by=INSPECT"
             .setFilter("supported_by=INSPECT")
             // BCP-47 language code for localized infoType friendly names.
             // Defaults to "en_US"
             .setLanguageCode("en-US")
             .build();

     // Use the client to send the API request.
     ListInfoTypesResponse response = dlpClient.listInfoTypes(listInfoTypesRequest);

     // Parse the response and process the results
     System.out.println("Infotypes found:");
     for (InfoTypeDescription infoTypeDescription : response.getInfoTypesList()) {
       System.out.println("Name : " + infoTypeDescription.getName());
       System.out.println("Display name : " + infoTypeDescription.getDisplayName());
     }
   }
 {{< /tab >}}
{{< /tabpane >}}

## Code 

### Useful comments
Comments should be used as needed, and should follow the following guidelines:
* Comments should add context not otherwise obvious from the code.
* Comments should be readable and grammatically correct.
* For values that the user may wish to configure, provide links to
 documentation that lists available options (and when to use them).
 
### Method Structure
Method arguments should be limited to what is absolutely required for testing.
In most cases, this is project specific information or the path to an external
file. For example, project specific information (such as `projectId`) or a
`filePath` for an external file is acceptable, while an argument for the type of
a file or a specific action is not.
 
Any declared function arguments should include a no-arg, main method with
examples for how the user can initialize the method arguments and call the
entrypoint for the snippet. If the values for these variables need to be
replaced by the user, be explicit that they are example values only.

Methods should avoid a return type whenever possible. Instead, show the user how
to interact with a returned object programmatically by printing some example
attributes to the console.

{{< tabpane langEqualsHeader=true >}}
 {{< tab header="Java" >}}
    public static void main(String[] args) {
        // TODO(developer): Replace these variables before running the sample.
        String projectId = "my-project-id";
        String filePath = "path/to/image.png";
        inspectImageFile(projectId, filePath);
    }

    // This is an example snippet for showing best practices.
    public static void exampleSnippet(String projectId, String filePath) {
        // Snippet content ...
    }
{{< /tab >}}
{{< /tabpane >}}


### Authentication
 
Samples should use authenticate using [Application Default Credentials][ADC].
 
If the code snippet is platform specific, explicitly show how to use that
platform's credentials.
 
{{< tabpane langEqualsHeader=true >}}
 {{< tab header="Java" >}}
   // Most clients use ADC by default. However, if your application needs to showcase a specific
   // credential source, show users how to do that explicitly.
   GoogleCredentials credentials = GoogleCredentials.fromStream(new FileInputStream("/path/to/credentials.json"));
{{< /tab >}}
{{< /tabpane >}}
 
[ADC]: (https://cloud.google.com/docs/authentication/production)

### Initializing Clients
 
Code snippets should show users how to initialize (and clean up, if necessary)
clients used by the user. Additionally, clients should contain a comment
clarifying proper usage (such as if clients should be reused for multiple
requests or if they are thread-safe).
 
{{< tabpane langEqualsHeader=true >}}
 {{< tab header="Java" >}}
   // Initialize client that will be used to send requests. This client only needs to be created
   // once, and can be reused for multiple requests. After completing all of your requests, call
   // the "close" method on the client to safely clean up any remaining background resources,
   // or use "try-with-close" statement to do this automatically.
   try (CloudClient dlp = CloudClient.create()) {
     // make a request with the client
   }
{{< /tab >}}
{{< /tabpane >}}

## Testing

// TODO

## Additional best practices

// TODO: Language specific? 