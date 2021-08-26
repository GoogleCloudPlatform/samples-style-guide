+++
title = "Samples Style Guide"
linkTitle = "Samples Style Guide"

+++


# Samples Style Guide

## Introduction


### Goals

## Sample Structure

### Region Tags

Each snippet should be be contained in its own file, with region tags including
all imports used in the sample.

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

### Region Tags 2

Each snippet should be be contained in its own file, with region tags including
all imports used in the sample.

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