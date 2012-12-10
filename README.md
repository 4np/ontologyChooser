Ontology Chooser
================

The Ontology Chooser integrates with the [NCBO](http://www.bioontology.org/about-ncbo) (National Center for Biomedical Ontology) [Ontologies](http://bioportal.bioontology.org/ontologies/) and builds upon the jQuery-ui autocomplete functionality.

Usage
=====
First of all, you need to make sure you have included jQuery, jQuery-ui (with autocomplete), the jQuery-ui autocomplete HTML extension and the Ontology Chooser itself. For example:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js" type="text/javascript"></script>
<link href="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8.16/themes/cupertino/jquery-ui.css" type="text/css" rel="stylesheet" /><script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.8.16/jquery-ui.min.js" type="text/javascript"></script>
<script src="https://github.com/scottgonzalez/jquery-ui-extensions/raw/master/autocomplete/jquery.ui.autocomplete.html.js" type="text/javascript"></script>
<script src="https://trac.nbic.nl/grails-plugins/browser/gdt/trunk/web-app/js/ontology-chooser.min.js?format=txt" type="text/javascript"></script>
```

_Note: this example uses hosted versions, you are advised to get download and use your own copies locally._

Within your page, you can define your form text input fields to be ontology fields by adding a rel tag:

```html
<input type="text" name="..." rel="ontologies-all" />
<input type="text" name="..." rel="ontologies-1132" />
<input type="text" name="..." rel="ontologies-1000,1031" />
```
The first input element will use all available ontologies, while the second one only uses the NCBO Species Ontology which has Ontology ID 1132 (as shown in the live demo above). The third uses two ontologies, both the Mouse adult gross anatomy (Ontology ID: 1000) as well as the Mouse pathology (Ontology ID: 1031). All available ontologies can be found at the NCBO BioPortal website.

To actually attach the Ontology Chooser to the ontology fields you need to instantiate the Ontology Chooser using Javascript when the DOM (Document Object Model) is ready like this:

```js
<script type="text/javascript">
// jQuery way to execute code when DOM is ready
$(document).ready(function() {
        // initialize the ontology chooser
        new OntologyChooser().init();
});
</script>
```

After Initialization
====================
After initializing the ontology fields and selecting one of the provided suggestions in the ontology autocomplete list, three hidden fields will be automatically inserted (if they do not yet exist) into the DOM. Or (if they do exist) their values will be changed accordingly:

```html
<input type="hidden" name="fieldName-concept_id" value="..."/>
<input type="hidden" name="fieldName-ontology_id" value="..."/>
<input type="hidden" name="fieldName-ncbo_id" value="..."/>
<input type="hidden" name="fieldName-full_id" value="..."/>
```
Where fieldName is the name of the corresponding ontology field. Upon selecting one of the provided term suggestions these hidden fields will be filled and, after submitting the form, can be handled in server side scripts.

Changing the look and feel
==========================
The following style sheet elements are used by the ontology chooser and can be used to tweak the look and feel:

```css
.ui-autocomplete .ui-menu-item {
        font-size: 10px;
}
.ui-autocomplete .about {
        font-size: 8px;
        color: #006DBA;
}
.ui-autocomplete .from {
        font-size: 8px;
        color: #666;
}
```

License
=======
This code is released under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0) and was initially developed to be used in the [Phenotype Database](http://phenotypefoundation.org/) as a replacement for the NCBO’s own [javascript implementation](http://www.bioontology.org/wiki/index.php/Ontology_Widgets#Term-selection_field_on_a_form).

Requirements:
=============
[jQuery](http://jquery.com/)
[jQuery-ui](http://jqueryui.com/download) (with the autocomplete widget)
[jQuery-ui autocomplete HTML extension](https://github.com/scottgonzalez/jquery-ui-extensions/blob/master/autocomplete/jquery.ui.autocomplete.html.js) ([direct download](https://github.com/scottgonzalez/jquery-ui-extensions/raw/master/autocomplete/jquery.ui.autocomplete.html.js))
