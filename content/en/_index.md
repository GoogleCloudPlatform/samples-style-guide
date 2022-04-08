---
title: "Effecive Samples"
linkTitle: "Style Guide"
type: docs
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

### Principles

Where the guidelines below are insufficient, these principles apply in
descending order of priority:
1. **Clarity**: The code's purpose and rationale is clear to the reader
2. **Idiomaticity**: The code should be written using idiomatic,
   community-driven coding practices
3. **Consistency**: The code has the same implementation from language to
   language
4. **Simplicity**: The code accomplishes its goal in the simplest way possible
5. **Portability**: The code should be able to run locally or in the Cloud
6. **Maintainability**: The code is written such that it can be easily
   maintained

## Structure

### Region tags
 
Each code snippet should have a region tag to define which parts of the snippet
are displayed from the documentation. Each region tag should be:
* Globally unique
* Consistent across the same snippets in different languages
* Begins with the product's region tag prefix
* In snake case

Region tags should show as much of the sample as possible, so that a user can
easily copy and paste the sample into their own environment to run it. 

### Imports
 
Samples should include any imports used in the sample.
 
This is easiest to enforce/detect when the samples are in their own file, so
samples should be structured as such unless there is a compelling reason not to.
 
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

def example_snippet() -> None:
      # Snippet Content ...

# [END product_example]
{{< /tab >}}
{{< tab header="Node.js" >}}
// [START product_example]
const resource = require('@google-cloud/example');

const exampleSnippet = function() {
    // Snippet content ...
}
// [END product_example]
{{< /tab >}}
{{< tab header="C#" >}}
// [START product_example]
using System;

public class ExampleSnippet
{   
    // Snippet methods ...
}
// [END product_example]

{{< /tab >}}
{{< tab header="Ruby" >}}
# [START product_example]
require "example/resource"

def example_snippet
  # Snippet Content ...
end     

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
{{< tab header="Python" >}}
"""
Moves a persistent disk from one zone to another.

See https://cloud.google.com/compute/docs/quickstart-client-libraries before running the code snippet.
"""
{{< /tab >}}
{{< tab header="Node.js" >}}
/**
* Moves a persistent disk from one zone to another.
*
* See https://cloud.google.com/compute/docs/quickstart-client-libraries before running the code snippet.
*/
{{< /tab >}}
{{< tab header="C#" >}}
// Moves a persistent disk from one zone to another.

// See https://cloud.google.com/compute/docs/quickstart-client-libraries before 
// running the code snippet.
{{< /tab >}}
{{< tab header="Ruby" >}}
# Moves a persistent disk from one zone to another.
#
# See https://cloud.google.com/compute/docs/quickstart-client-libraries before running the code snippet.
{{< /tab >}}
{{< /tabpane >}}

### Minimal arguments

Method arguments should be limited to what is absolutely required for testing.
In most cases, this is project specific information or the path to an external
file. For example, project specific information (such as `projectId`) or a
`filePath` for an external file is acceptable, while an argument for the type of
a file or a specific action is not.
 
{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// This is an example snippet for showing best practices.
public static void exampleSnippet(String projectId, String filePath) {
    // Snippet content ...
}
{{< /tab >}}
{{< tab header="Python" >}}
# This is an example snippet for showing best practices.
def example_snippet(project_id: str, file_path: str) -> None:
    # Snippet content ...
{{< /tab >}}
{{< tab header="Node.js" >}}
function main() {
  // This argument is required, and should be declared
  const requiredArg = '...';

  exampleSnippet(requiredArg)
}

const exampleSnippet = function(requiredArg) {
  // Snippet content...
}
{{< /tab >}}
{{< tab header="C#" >}}
// This is an example snippet for showing best practices.
public void Example(
    string projectId = "my-project-id,
    string filePath = "path/to/image.png")
{
    // Snippet content ...
}
{{< /tab >}}
{{< tab header="Ruby" >}}
# This is an example snippet for showing best practices.
def example_snippet project_id:, file_path:
  # Snippet content ...
end
{{< /tab >}}
{{< /tabpane >}}

### Process the result

Methods should avoid a return type whenever possible. Instead, show the user how
to interact with a returned object programmatically by printing some example
attributes to the console. Tests should use the output of the function to
ensure that it works.

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// This is an example snippet for showing best practices.
public static void exampleSnippet(String projectId, String filePath) {
    // Snippet content ...
}
{{< /tab >}}
{{< tab header="Python" >}}
# This is an example snippet for showing best practices.
def example_snippet(project_id: str, file_path: str -> None):
    # Snippet content ...
{{< /tab >}}
{{< tab header="Node.js" >}}
const exampleSnippet = function(projectId, filePath) {
  // Snippet content ...
  // (This snippet should not `return` anything.)
}
{{< /tab >}}
{{< tab header="Ruby" >}}
def example_snippet project_id:, file_path: 
  # Snippet content ...
  response = client.example_action example_action_request
  puts "Got the following response #{response.details}"
end
{{< /tab >}}
{{< tab header="C#" >}}
// This is an example snippet for showing best practices.
public void Example(
    string projectId = "my-project-id,
    string filePath = "path/to/image.png")
{
    // Snippet content ...
    Console.WriteLine($"Example {data} for project: {projectId}");
}
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
 returned as expected. This is typically done by printing some aspects of the
 response to stdout.

The samples below show this in action.

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
    System.out.println("Info types found:");
    for (InfoTypeDescription infoTypeDescription : response.getInfoTypesList()) {
      System.out.println("Name : " + infoTypeDescription.getName());
      System.out.println("Display name : " + infoTypeDescription.getDisplayName());
    }
  }
}  
{{< /tab >}}
{{< tab header="Python" >}}
def list_info_type(
    language_code: Optional[str] = "en-US",
    result_filter: Optional[str] = "supported_by=INSPECT",
 -> None):
    """List types of sensitive information within a category."""

    # Initialize client that will be used to send requests. This client only
    # needs to be created once, and can be reused for multiple requests. After
    # completing all of your requests, call the "__exit__" method on the client to
    # safely clean up any remaining background resources. Alternatively, use the
    # client as a context manager. A single client can be shared across multiple threads.
    # In multiprocessing# scenarios, create client instances after forking.
    dlp_client = dlp_v2.DlpServiceClient()

    request = dlp_v2.ListInfoTypesRequest(
        # An optional filter to only return info types supported
        # by certain parts of the API. Supported filters are 
        # "supported_by=INSPECT" and "supported_by=RISK_ANALYSIS". Defaults
        # to "supported_by=INSPECT".
        filter=result_filter,
        # The BCP-47 language code to use, e.g. 'en-US'.
        language_code=language_code,
    )

    # Use the client to send the API request
    info_types = dlp_client.list_info_types(request)

    # Parse the response and process the results
    print("Infotypes found:")
    for info_type in info_types:
        print(f"Name: {info_type.name}")
        print(f"Display name: {info_type.display_name}")
{{< /tab >}}
{{< tab header="Node.js" >}}
// Imports the Google Cloud Data Loss Prevention library
const {DlpServiceClient} = require('@google-cloud/dlp');

// Instantiates a reusable client object
const dlpClientInstance = new DlpServiceClient();

// Lists the types of sensitive information the DLP API supports.
async function listInfoTypes() {
  // Only return infoTypes supported by certain parts of the API.
  // Supported filters are:
  //   "supported_by=INSPECT"
  //   "supported_by=RISK_ANALYSIS"
  const filter = 'supported_by=INSPECT';

  // BCP-47 language code for localized infoType friendly names.
  // Defaults to "en_US"
  languageCode = 'en-us';

  // Perform the API request.
  const [response] = await dlpClientInstance.listInfoTypes({
    languageCode,
    filter
  });

  // Parse the response and process the results.
  const infoTypes = response.infoTypes;
  console.log('Info types:');
  infoTypes.forEach(infoType => {
    console.log(`\t${infoType.name} (${infoType.displayName})`);
  });
}
{{< /tab >}}
{{< tab header="C#" >}}
// Lists the types of sensitive information the DLP API supports.
public ListInfoTypesResponse ListInfoTypes(
    string languageCode = "en-US",
    string filter = "supported_by=INSPECT")
{
    // Initialize the client that will be used to send requests. This client only needs to be created
    // once, and can be reused for multiple requests.
    var dlp = DlpServiceClient.Create();
    // Use the client to send the API request.
    var response = dlp.ListInfoTypes(
        // Construct the request to be sent by the client.
        new ListInfoTypesRequest
        {
            LanguageCode = languageCode,
            Filter = filter
        });

    // Parse the response and process the results.
    Console.WriteLine("Info Types:");
    foreach (var InfoType in response.InfoTypes)
    {
        Console.WriteLine($"\t{InfoType.Name} ({InfoType.DisplayName})");
    }

    return response;
}
{{< /tab >}}
{{< tab header="Ruby" >}}
# Lists the types of sensitive information the DLP API supports.
def list_info_types

  # Initialize client that will be used to send requests.
  dlp_client = Google::Cloud::Dlp.dlp_service

  # Construct the request to be sent by the client 
  list_info_types_request = { 
    # BCP-47 language code for localized info_type friendly names.
    # Defaults to "en_US"
    parent: "en-US", 
    
    # Supported filters are "supported_by=INSPECT" and "supported_by=RISK_ANALYSIS"
    # Defaults to "supported_by=INSPECT"
    filter: "supported_by=INSPECT" 
  }

  # Use the client to send the API request.
  list_info_types_response = dlp_client.list_info_types request

  # Parse the response and process the results
  puts "Info types found:"
  list_info_types_response.info_types.each do |info_type|
    puts "Name : #{info_type.name}"
    puts "Display name: #{info_type.display_name}"
  end
end
{{< /tab >}}
{{< /tabpane >}}

### No CLIs

Do not include CLIs for running your sample. We expect developers to copy and
paste code directly from cloud.google.com into their own environment. Adding
CLIs has historically been expensive to maintain in the past, and detracts from
the purpose of the snippet itself.

## Code 

### Useful comments

Comments should be used as needed, and should follow the following guidelines:
* Comments should add context not otherwise obvious from the code.
* Comments should be readable and grammatically correct.
* For values that the user may wish to configure, provide links to
 documentation that lists available options (and when to use them).

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
{{< tab header="Python" >}}
# Most clients use ADC by default. However, if your application needs to
# showcase a specific credential source, show users how to do that explicitly.
from google.oauth2 import service_account

credentials = service_account.Credentials.from_service_account_file(
  "/path/to/credentials.json"
)
{{< /tab >}}
{{< tab header="Node.js" >}}
// Most clients use ADC by default. However, if your application needs to showcase a specific
// credential source, show users how to do that explicitly.
const keyFile = '/path/to/credentials.json';
const auth = new GoogleAuth({
  keyFile: keyFile,
  scopes: 'https://www.googleapis.com/auth/cloud-platform',
});
{{< /tab >}}
{{< tab header="C#" >}}
// All clients use ADC by default. However, if your application needs to showcase a specific
// credential source, show users how to do that explicitly.
var credentials = GoogleCredential.FromFile("/path/to/credentials.json");
{{< /tab >}}
{{< tab header="Ruby" >}}
require "google/cloud/spanner"

# Most clients use ADC by default. However, if your application needs to showcase a specific
# credential source, show users how to do that explicitly.
Google::Cloud::Spanner.configure do |config|
  config.project_id  = "my-project-id"
  config.credentials = "path/to/keyfile.json"
end

client = Google::Cloud::Spanner.new
{{< /tab >}}
{{< /tabpane >}}
 
[ADC]: (https://cloud.google.com/docs/authentication/production#automatically)

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
{{< tab header="Python" >}}

# NOTE FOR SAMPLE AUTHOR: 
# **DO NOT include this comment block in the sample.**
# The comment below about clients applies to gRPC-based clients (clients with GAPIC_AUTO in .repo-metadata.json). For google-api-python-client, see https://googleapis.github.io/google-api-python-client/docs/thread_safety.html#the-httplib2http-objects-are-not-thread-safe. For other libraries, consult with
# the library owner.

# Initialize client that will be used to send requests across threads. This 
# client only needs to be created once, and can be reused for multiple requests.
# After completing all of your requests, call the "__exit__()" method to safely 
# clean up any remaining background resources. Alternatively, use the client as 
# a context manager.
with dlp_v2.DlpServiceClient() as dlp_client:
    # make a request with the client
{{< /tab >}}
{{< tab header="Node.js" >}}
// Imports the Google Cloud Data Loss Prevention library
const {DlpServiceClient} = require('@google-cloud/dlp');

// Instantiates a reusable client object in the global scope.
// (Node.js will automatically clean it up when the script terminates.)
const dlpClientInstance = new DlpServiceClient();
{{< /tab >}}
{{< tab header="C#" >}}
// Initialize the client that will be used to send requests. This client only needs to be created
// once, and can be reused for multiple requests across your entire application.

var client = Server.CreateClient();
// make a request with the client.

// If for any reason the client lifetime needs to be scoped to a single method,
// you can use a "using" statement or a "using" declaration.

// Example "using" statement.
using (var client = Server.CreateClient())
{
    // make a request with the client.
}

// Example "using" declaration, which will dispose of the resource
// when execution falls outside the enclosing statement block.
public void ExampleMethod()
{
    using var client = Server.CreateClient();
    // make a request with the client.
}
{{< /tab >}}
{{< tab header="Ruby" >}}
require "google/cloud/spanner"

# Initialize client that will be used to send requests. This client only needs to be created
# once, and can be reused for multiple requests. After completing all of your requests, call
# the "close" method on the client to safely clean up any remaining background resources.
spanner = Google::Cloud::Spanner.new
spanner_client = spanner.client spanner_instance_id, spanner_database_id
spanner_client.close
{{< /tab >}}
{{< /tabpane >}}

### Cyclomatic Complexity

Cyclomatic complexity is the measure of possible code paths. The more code
paths, the more complex the code snippet, and the harder to understand and test.
Flow control statements like conditionals (if/else), switches, and loops are
examples of code that increases cyclomatic complexity.
	
Code snippets should have a single path demonstrating their purpose with no
extra code.

### Error Handling

Samples should include examples and details of how to catch and handle common
errors that are the result of improper interactions with the client or service. 

If there is no solution (or if the solution is too verbose to resolve in a
sample) it is acceptable to either log or leave a comment explaining what the
developer should do.

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// Always catch the most specific type of Exception, instead of a more general one.
try {
  // Do something
} catch (IllegalArgumentException ok) {
  // IllegalArgumentException's are thrown when an invalid argument has been passed to a function. Ok to ignore.
}
{{< /tab >}}
{{< tab header="Python" >}}
# Catch the most specific type of Exception, instead of a more general one.
try:
    bucket = storage_client.get_bucket(bucket_name)
    bucket.delete()
except google.api_core.exceptions.NotFound:
    # NOTE TO SAMPLE AUTHOR: Make sure to log errors rather than silentily ignore
    print(f"Resource '{name}' already deleted.")
{{< /tab >}}
{{< tab header="Node.js" >}}
// Unhandled exceptions will cause Node.js to crash. Log exception
// messages via console.error(), and handle any non-fatal exceptions.
try {
  // Do something
} catch (e) {
  // Log the error to stdout
  console.error('Error:', e.message);

  // Reraise any fatal exceptions
  if (/* exception is fatal */) {
    throw e
  }
}
{{< /tab >}}
{{< tab header="C#" >}}
try
{
    // Do something
}
catch (ArgumentException e)
{
    //ArgumentException's are thrown when one of the arguments provided to a method is not valid.
    Console.WriteLine(e.Message);
}
{{< /tab >}}
{{< tab header="Ruby" >}}
# Catch the most specific type of Exception, instead of a more general one.
begin
  # Do something
rescue Google::Cloud::AlreadyExistsError
  # Do nothing if it already exists
end
{{< /tab >}}
{{< /tabpane >}}

### Linting

Our code snippets should adhere to a style used by the language communities. We
should prefer using standard linters that are popular in the community to
enforce style.

### Portability

Each of the major operating systems are well-represented among GCP users. To
provide a good experience for most GCP users, our code snippets need to work on
multiple operating systems. In addition, our code snippets may be executed in
multiple hosting environments, such as GCF, GAE, GKE, GCE, AWS, and local
machines.

Where possible, code snippets should work across environments and hosting
platforms. Code snippets should point out any differences between platforms via
code comments and use platform-agnostic libraries and code constructs.

For example, a code snippet that:

* Uses the language’s standard path library to construct file paths
* Does not directly rely on POSIX system calls
* Handles code-sensitivity differences
* Avoids platform-specific APIs

## Testing

### Coverage
Code snippets should have reasonable test coverage and all critical code paths
should have integration tests that test against the production service. 

## Additional best practices

### Adhere to language idioms

Code snippets should use preferred code patterns that are idiomatic to the
particular language (e.g. promises, futures, static API calls from singletons,
builders, etc).

Aside: Note that in being idiomatic we can end up creating code snippets that
are radically different from language-to-language. Err on the side of what is
idiomatic to the language, though cross-language consistency does not hurt.

Use features that work in all GCP-supported versions of a language and use
language idioms that the community understands. Generally, do things “the way
the community does it”.

## Language-specific practices

{{< content-tabpane >}}
{{< content-tab header="Java" >}}

### Easy run function

Any declared function arguments should include a no-arg, main method with
examples for how the user can initialize the method arguments and call the
entrypoint for the snippet. If the values for these variables need to be
replaced by the user, be explicit that they are example values only. Wherever
possible, provide a link to documentation that enumartes the options.


{{< highlight java >}}
// [START product_example]
import com.example.resource;

public static void main(String[] args) {
    // TODO(developer): Replace these variables before running the sample.
    String projectId = "my-project-id";
    String filePath = "path/to/image.png";
    exampleSnippet(projectId, filePath);
}

// This is an example snippet for showing best practices.
public static void exampleSnippet(String projectId, String filePath) {
    // Snippet content ...
}
// [END product_example]
{{< / highlight >}}

{{< /content-tab >}}

{{< content-tab header="Python" >}}
// TODO
{{< /content-tab >}}

{{< content-tab header="Go" >}}
// TODO
{{< /content-tab >}}

{{< content-tab header="Nodejs" >}}
// TODO
{{< /content-tab >}}

{{< content-tab header="C#" >}}
// TODO
{{< /content-tab >}}

{{< content-tab header="PHP" >}}
// TODO
{{< /content-tab >}}

{{< content-tab header="Ruby" >}}
// TODO
{{< /content-tab >}}
{{< /content-tabpane >}}