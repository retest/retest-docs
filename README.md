# retest-docs

This is the documentation of retest, which can be found at https://retest.de/docs/.

## Contributing

You are invited to correct errors or improve the documentation otherwise. In order to do so, open an
[issue](https://github.com/retest/retest-docs/issues) or create a [pull
request](https://github.com/retest/retest-docs/pulls). In the latter case, please follow the [GitHub
Flow](https://guides.github.com/introduction/flow/) guidelines and hard wrap lines at column 120. Furthermore, you must
sign the [contributor license agreement](https://www.clahub.com/agreements/retest/retest).

### Modifying an existing page

Go ahead... .

### How to reference icons, images and pages

Icons are placed inside `/icons`. Standard markdown image reference can be used: `![Warning](icons/warning.png)`. Images are usually placed inside the pages' directory.

References to other pages are addressed with relative paths. They address the markdown page: `[english site](en/index.md)`.

### Creating a new page

When creating a new page it should be placed inside a corresponding folder:
Folder | Description
--     | --
extensions | How retest can be extended
howtos | How-to articles
configuration/konfiguration | Configuration for retest and additional tools
recapture | Everything that has to do with the module *recapture*
replay | Everything that has to do with the module *replay*
review | Everything that has to do with the module *review*
surili | Everything that has to do with the module *surili*
testprozess | What is testing

A new page should have the following template:
```
{% extends "[Template].tmpl" %}
{% block primary %}

[Here goes your content]

{% endblock primary %}
```
The `Template` should be replace according to the name of the `.tmpl` file inside the folder where the page was created. If there is no such file then the parent `.tmpl` file should be used (e.g `de-docs-content.tmpl`).

Each file should be listed inside the corresponding `index.md` file, so that readers can navigate to the page. If necessary it should also be listed in the language root `index.md` (e.g `de/index.md`).