---
title: "Effective Samples"
linkTitle: "Style Guide"
type: docs
weight: 20
---

## Introduction {#introduction}

This document defines samples standards for "standalone" code snippets.
It encourages recommended practices for authoring code intended to teach others.
By consistently applying these practices, the collection of samples as a whole
become more approachable.

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

### Principles {#principles}

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

Code snippets should use preferred code patterns that are idiomatic to the
particular language (e.g. promises, futures, static API calls from singletons,
builders, etc). This may result in code snippets that are radically different
from language-to-language. Err on the side of what is idiomatic to the language,
though cross-language consistency does not hurt. Generally, do things
“the way the community does it”.

## Structure {#structure}

### Region tags {#region-tags}

Each code snippet should have a region tag to define which parts of the snippet
are displayed from the documentation. Each region tag should be:

* Globally unique
* Consistent across the same snippets in different languages
* Begins with the product's region tag prefix
* In snake case (`snake_case`)

Region tags should show as much of the sample as possible, so that a user can
easily copy and paste the sample into their own environment to run it.

### Imports {#imports}

Samples should include any imports statements the code depends on.

This is easiest to enforce/detect when the samples are in their own file, see
the [one sample per file](#one-per-file) guideline.

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
{{<tab header="Go">}}
package example

// Region tags should start after the package, but before imports.
// [START product_example]
import "example.com/resource"

func exampleSnippet() error {
    // Snippet Content ...
}

// [END product_example]
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
{{< tab header="PHP" >}}
// [START product_example]
use Example\Resource

function example_snippet() {
    // Snippet Content ...
}
// [END product_example]
{{< /tab >}}
{{< /tabpane >}}

### One sample per file {#one-per-file}

A single file should only include one sample. This shows the minimal
set of dependencies via import statements, keeps the end-to-end code relevant
to the reader's current learning need, and helps reviewers validate the
 [imports](#imports) guideline.

### Sample description {#description}

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
{{< tab header="Go" >}}
// exampleSnippet moves a persistent disk from one zone to another.
//
// Comments should follow the best practices described in
// https://golang.org/doc/effective_go.html#commentary.
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
{{< tab header="PHP" >}}
/**
 * Moves a persistent disk from one zone to another.
 *
 * See https://cloud.google.com/compute/docs/quickstart-client-libraries
 * before running the code snippet.
 */
{{< /tab >}}
{{< /tabpane >}}

### Minimal arguments {#minimal-arguments}

Method arguments should be limited requirements for testing. In most cases, this
is project-specific information (`projectID`) or the path to an external file (`filePath`).

Do not use arguments for values that can be hard-coded, such as the type of a
file or an operation to perform.

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// This is an example snippet for showing best practices.
public static void exampleSnippet(String projectId, String filePath) {
    // Snippet content ...
}
{{< /tab >}}
{{< tab header="Go" >}}
// exampleSnippet demonstrates best practices.
func exampleSnippet(projectID, filePath string) error {
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
{{< tab header="PHP" >}}
// This is an example snippet for showing best practices.
function example_snippet(string $projectId, string $filePath): void
{{< /tab >}}
{{< /tabpane >}}

### Process the result {#result}

Methods should avoid a return type whenever possible. Instead, show the user how
to interact with a returned object programmatically by printing example
attributes to the console. Tests should use the output of the function to ensure
that it works.

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// This is an example snippet for showing best practices.
public static void exampleSnippet(String projectId, StringfilePath) {
    // Snippet content ...
}
{{< /tab >}}
{{< tab header="Go" >}}
// exampleSnippet demonstrates best practices.
// The function prints to an io.Writer for testing purposes. Do not print to
// stdout or stderr. Use the io.Writer instead.
func exampleSnippet(w io.Writer, projectID, filePath string) error {
    // Snippet content ...
    // Using the io.Writer looks like this:
    fmt.Fprintf(w, "The answer is %v\n", 42)
}
{{< /tab >}}
{{< tab header="Python" >}}
# This is an example snippet for showing best practices.
def example_snippet(project_id: str, file_path: str) -> None:
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
{{< tab header="PHP" >}}
// This is an example snippet for showing best practices.
function example_snippet(string $projectId, string $filePath): void
{
    // Snippet content ...
    printf(
        'Response values: %s, %s',
        $response->getExampleName(),
        $response->getExampleValue()
    );
}
{{< /tab >}}
{{< /tabpane >}}

### Arrange, Act, Assert {#pattern}

Most samples should follow the "Arrange, Act, Assert" pattern as closely as
possible. Composing samples into these discrete steps makes them more
approachable to beginners:

1. **Arrange** - Create and configure the components for the request. Avoid
 nesting these components beyond 2-3 levels, it makes understanding the code
 more difficult.
2. **Act** - Send the request to the service and receive a response.
3. **Assert** - Verify that the call was successful and that the expected
 response was returned. This is typically done by [printing some of the
 response to stdout](#result).

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
  ) -> None:
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
{{< tab header="Go" >}}
import (
    "context"
    "fmt"

    dlp "cloud.google.com/go/dlp/apiv2"
    dlppb "google.golang.org/genproto/googleapis/privacy/dlp/v2"
)

// listInfoTypes lists the types of sensitive information the DLP API supports.
func listInfoTypes(w io.Writer) error {
    ctx := context.Background()
    // Initialize a client once and reuse it to send multiple requests. Clients
    // are safe to use across goroutines. When the client is no longer needed,
    // call the Close method to cleanup its resources.
    c, err := dlp.NewClient(ctx)
    if err != nil {
        fmt.Fprintf(w, "failed to initialize dlp.Client: %v", err)
        return err
    }
    defer c.Close()

    // Construct the request to be sent by the client
    req := &dlppb.ListInfoTypesRequest{
        // Only return infoTypes supported by certain parts of the API.
        // Supported filters are "supported_by=INSPECT" and "supported_by=RISK_ANALYSIS"
        // Defaults to "supported_by=INSPECT"
        Filter: "supported_by=INSPECT",
        // BCP-47 language code for localized infoType friendly names.
        // Defaults to "en_US"
        LanguageCode: "en-US",
    }

    resp, err := c.ListInfoTypes(ctx, req)
    if err != nil {
        fmt.Fprintf(w, "c.ListInfoTypes failed: %v", err)
        return err
    }
    fmt.Fprintln(w, "Infotypes found:")
    for _, t := range resp.InfoTypes {
        fmt.Fprintf(w, "Name: %s\n", t.Name)
        fmt.Fprintf(w, "Display name: %s\n", t.DisplayName)
    }
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
{{< tab header="PHP" >}}
use Google\Cloud\Dlp\V2\DlpServiceClient;

/**
 * Lists all Info Types for the Data Loss Prevention (DLP) API.
 */
function list_info_types(): void
{
    // Arrange: Instantiate a client.
    $dlp = new DlpServiceClient();

    // Arrange: Prepare the request parameters.
    $params = [
        // Only return infoTypes supported by certain parts of the API.
        // Supported filters: "supported_by=INSPECT" and "supported_by=RISK_ANALYSIS"
        'filter' =>'supported_by=INSPECT',

        // BCP-47 language code for localized infoType friendly names.
        // Defaults to "en_US"
        'languageCode' => 'en-US'
    ];

    // Act: Run the request.
    $response = $dlp->listInfoTypes($params);

    // Assert: Print the results.
    print('Info Types:' . PHP_EOL);
    foreach ($response->getInfoTypes() as $infoType) {
        printf(
            '  %s (%s)' . PHP_EOL,
            $infoType->getDisplayName(),
            $infoType->getName()
        );
    }
}
{{< /tab >}}
{{< /tabpane >}}

### No CLIs {#no-cli}

Do not include CLIs for running your sample. We expect developers to copy and
paste code directly from cloud.google.com into their own environment.

Previous practice shows CLIs are expensive to maintain and detracts from the
purpose of the snippet.

## Code {#code}

### Language compatibility {#lang-compat}

Use features that work in all GCP-supported versions of a language and use
language idioms that the community understands.

### Useful comments {#comments}

Comments should be used as needed with the following guidelines:

* Comments should add context not otherwise obvious from the code.
* Comments should be readable and grammatically correct.
* For values that the user may wish to configure, provide links to
 documentation that lists available options (and when to use them).

### Authentication {#authentication}

Samples should always authenticate using [Application Default Credentials][ADC].
Most clients do this automatically, and no special steps are required.

If the code snippet is platform specific, explicitly show how to use that
platform's credentials.

[ADC]:https://cloud.google.com/docs/authentication/production#automatically

{{< tabpane langEqualsHeader=true >}}
{{< tab header="Java" >}}
// Most clients use ADC by default. However, if your application needs to showcase a specific
// credential source, show users how to do that explicitly.
GoogleCredentials credentials = GoogleCredentials.fromStream(new FileInputStream("/path/to/credentials.json"));
{{< /tab >}}
{{< tab header="Go" >}}
// Most clients use ADC by default. However, if your application needs to
// showcase a specific Go credential source, show users how to do that
// explicitly.
ctx := context.Background()
foo.NewClient(ctx, option.WithCredentialsFile("/path/to/credentials.json"))
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
{{< tab header="PHP" >}}
// Most clients use ADC by default. However, if your application needs to showcase a specific
// credential source, show users how to do that explicitly.
$config = [
    'keyFilePath' => '/path/to/credentials.json',
    'projectId' => $projectId,
];
$storage = new StorageClient($config);
{{< /tab >}}
{{< /tabpane >}}

### Initializing Clients {#clients}

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
{{< tab header="Go" >}}
// Initialize a client once and reuse it to send multiple requests. Clients
// are safe to use across goroutines. When the client is no longer needed,
// call the Close method to cleanup its resources.
ctx := context.Background()
c, err := foo.NewClient(ctx)
if err != nil {
    fmt.Fprintf(w, "failed to initialize foo.Client: %v", err)
    return err
}
defer c.Close()

// make a request with the client...
{{< /tab >}}
{{< tab header="Python" >}}

# NOTE FOR SAMPLE AUTHOR:
# **DO NOT include this comment block in the sample.**
# The comment below about clients applies to gRPC-based clients (clients with GAPIC_AUTO in .repo-metadata.json). 
# For google-api-python-client, see 
# https://googleapis.github.io/google-api-python-client/docs/thread_safety.html#the-httplib2http-objects-are-not-thread-safe. 
# For other libraries, consult with the library owner.

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
{{< tab header="PHP" >}}
// Initialize client that will be used to send requests.
// This client only needs to be created once, reuse it for multiple requests.

$dlp = new DlpServiceClient();
{{< /tab >}}
{{< /tabpane >}}

### Cyclomatic Complexity {#complexity}

Cyclomatic complexity is the measure of possible code paths. The more code
paths, the more complex the code snippet, and the harder to understand and test.
Flow control statements like conditionals (if/else), switches, and loops are
examples of code that increases cyclomatic complexity.

Code snippets should have a single path demonstrating their purpose with no
extra code.

### Error Handling {#errors}

Samples should include examples and details of how to catch and handle common
errors that are the result of improper interactions between the client and service.

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
{{< tab header="Go" >}}
// If the sample can run into errors, write the error message to the provided
// io.Writer. Don't call log.Fatal or friends.
if err != nil {
    // TODO(developer): return or handle error as necessary
    fmt.Fprintf(w, "failed to initialize foo.Client: %v", err)
    return err
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
{{< tab header="PHP" >}}
// Catch the most specific type of Exception, instead of a more general one.
try {
    // Do something.
} catch (InvalidArgumentException $e) {
    // IllegalArgumentException is thrown when an invalid argument has been passed to a function.
}
{{< /tab >}}
{{< /tabpane >}}

### Linting {#linting}

Our code snippets should adhere to a style used by the language communities.
We prefer to enforce style using standard linters that are popular in
the community.

### Portability {#portability}

Each of the major operating systems are well-represented among GCP users. To
provide a good user experience, our code snippets need to work on multiple
operating systems.

Our code snippets may be executed in multiple hosting environments, such as
[App Engine][gae], [Cloud Functions][gcf], [Cloud Run][run],
[Kubernetes Engine][gke], [Compute Engine][gce], [Cloud Shell][shell],
other cloud providers, and local machines.

Where possible, code snippets should work across environments and hosting
platforms. Code snippets should point out any differences between platforms via
code comments and use platform-agnostic libraries and code constructs.

Examples of portable practices include:

* Use the language’s standard path library to construct file paths
* Do not directly rely on POSIX system calls
* Handle case-sensitivity differences
* Avoid platform-specific APIs

[gae]: https://cloud.google.com/appengine
[gcf]: https://cloud.google.com/functions
[run]: https://cloud.google.com/run
[gke]: https://cloud.google.com/kubernetes-engine
[gce]: https://cloud.google.com/compute
[shell]: https://cloud.google.com/shell

## Testing {#testing}

### Coverage {#coverage}

Code snippets should have reasonable test coverage and all critical code paths
should have integration tests that test against the production service.

## Language-specific practices {#language-specific}

{{< content-tabpane >}}
{{< content-tab header="Java" >}}

### Easy run function {#run-function}

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

### Easy run function

Samples with function parameters should show how to prepare parameter values
and call the function. Do this from a `callSample()` function below the main
sample code. Do not include significant logic in the `callSample()` function,
and do not write tests for it.

Direct the developer to change the parameter values from the provided examples.

Where possible, provide a link to documentation that explains the options.

{{<highlight PHP>}}
// [START product_example]

/**
 * Example snippet showing the easy run function rule.
 *
 * @param string $projectId         Google Cloud Project
 * @param string $filePath          Path to file for processing
 */
function example_snippet(string $projectId, string $filePath): void
{
    // Snippet content ...
}

/**
 * TODO(developer): Replace sample parameters before running the code.
 */
function callSample(): void
{
    $projectId = 'your-project-id';
    $filePath = 'path/to/image.png';
    example_snippet($projectId, $region);
}
// [END product_example]
{{< / highlight >}}

{{< /content-tab >}}

{{< content-tab header="Ruby" >}}
// TODO
{{< /content-tab >}}
{{< /content-tabpane >}}
