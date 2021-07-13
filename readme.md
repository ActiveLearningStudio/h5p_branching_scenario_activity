
# Branching Scenario reuse fix

Fix branching scenario crash on click of reuse

## Issues

```
1. When a user is creating a fresh branching scenario content type,
   the editor loads old libraries despite existing newer ones.

2. When a user reuses an existing branching scenario content type
   that utilizes H5P.BranchingScenario v1.2, the editor crashes.
```

## Solutions

```
1. There is function 'updateContentTypeCache()' available in the core of H5P
   in h5p.classes.php file. That function needs to be call for updating cache 
   of content type and newly added libraries.
   For reference please find details here ->
   https://github.com/h5p/h5p-editor-php-library/blob/master/h5peditor-ajax.class.php#L470

2. The reuse functionality working fine in firefox browser whereas 
   to use it in chrome, we need to update apache/config/mime.type
   file and have to add the following code:
 
       `application/x-h5p                   h5p
        application/zip zip                 h5p
        application/x-zip-compressed        h5p`

   OR

       Put `AddType application/x-h5p h5p` in .htaccess file
```