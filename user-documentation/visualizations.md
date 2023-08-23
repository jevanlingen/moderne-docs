# Getting started with visualizations

Visualizations provide a unique way of looking at the data generated by specific recipes. A visualization could be a complex image that you can zoom in and out of to examine connections between nodes or it could be as simple as a text-based table that you can filter or search (see the [examples section](#visualization-examples) to see what these look like).

In this guide, we will explain everything you need to know to find and use visualizations in the Moderne platform.

## Where visualizations exist

While you will see a visualization button on every recipe run, it will be disabled for most recipes. There are two main reasons for this:

1. Visualizations will not work on [repository groups](/references/managing-repository-groups.md). If you want to see visualizations, you **must** run the recipe against an organization instead:

  ![Visualization restrictions](/.gitbook/assets/visualization-restrictions.png)

2. Only a handful of recipes currently offer visualizations. You can see the list of visualizations in the [moderne-visualizations-misc repository](https://github.com/moderneinc/moderne-visualizations-misc/tree/main/moderne_visualizations_misc/specs) or you can use the following GraphQL query to find all visualizations:

```
query {
  visualizationCategories {
    visualizations {
      id
      name
      description
      recipe {
        id
      }
    }
  }
}
```

Below you can find some of the recipes that currently produce visualizations:

```
org.openrewrite.sql.FindSql
org.openrewrite.java.dependencies.DependencyVulnerabilityCheck
org.openrewrite.cobol.search.FindRelationships
org.openrewrite.gradle.search.FindGradleWrapper
org.openrewrite.cobol.search.FindCopybook
org.openrewrite.cobol.search.FindRelationships
org.openrewrite.FindSourceFiles
org.openrewrite.LanguageComposition
org.openrewrite.FindLstProvenance
org.openrewrite.LanguageComposition
org.openrewrite.java.search.FindMethods
```

## How to view visualizations

If a recipe produces a visualization, the `Visualizations` button will be blue and clickable after the recipe finishes running:

![Visualizations button](/.gitbook/assets/visualizations-button.png)

When you click on it, you'll be taken to a page that contains all of the visualizations available for that recipe. Some recipes may only have one visualization whereas others might have many:

![Visualizations list](/.gitbook/assets/visualizations-list.png)

Click on the one you want to execute. After you do, the visualization box will expand. Some visualizations will offer you options to choose from to tune the visualization to your needs:

![Visualization options](/.gitbook/assets/visualizations-options.png)

Visualization options serve two main purposes: they can change the rendering of the visualization (such as turning a node from a square to a circle) or they can subset the data (e.g., taking 1000 nodes and filtering them down to 100 that match your specific needs).

Once you've selected the options you want, click the `Run Visualization` button at the bottom:

![Run visualization](/.gitbook/assets/run-visualization.png)

This will trigger the process for building the visualization. Once it's done building, you should see the visualization appear:

![Visualization result](/.gitbook/assets/visualization-result.png)

{% hint style="warning" %}
If your recipe was canceled and didn't finish running, you will not be able to successfully produce a visualization. 
{% endhint %}

## Visualization examples

### Language composition report

![Language composition](/.gitbook/assets/language-composition-example.png)

### SQL operation usage in code

![SQL operation usage](/.gitbook/assets/sql-operation-usage.png)

### Dependency vulnerability profile

![Dependency vulnerability profile](/.gitbook/assets/dependency-vulnerability-profile.png)

### Gradle wrapper composition

![Gradle wrapper composition](/.gitbook/assets/gradle-wrapper-composition.png)

### Plugin versions used to build LSTs

![Plugin versions used to build LSTs](/.gitbook/assets/plugin-version-lsts.png)

### Find uses of method in code

![Find uses of method in code](/.gitbook/assets/find-method-uses.png)

### COBOL relationship diagram

![COBOL relationship diagram](/.gitbook/assets/cobol-relationships.png)

### COBOL relationship data grid

![COBOL relationship data grid](/.gitbook/assets/cobol-data-grid.png)
