# H5P_Standalone
This example shows how to make H5P work in standalone-mode.

![How to](https://github.com/CleanLake412/H5P_Standalone/blob/master/howto/howto.png?raw=true)

## How to unzip and deploy h5p files

- Please change extension of *.h5p files to *.rar.

	H5P/08_experiment-8.h5p  =>  H5P/08_experiment-8.rar
	H5P/09_qustion-9.h5p     =>  H5P/09_qustion-9.rar

- And extract *.rar files in same named folder respectively.

	H5P/08_experiment-8
	H5P/09_qustion-9

## How to display H5P frames in HTML

```html
<div id="h5p-container-8"></div>
<script>
  (function() {
    let h5pContainer = document.getElementById("h5p-container-8"); // div tag ID
    let h5pJsonPath = 'H5P/08_experiment-8'; // H5P data directory path

    if (!document.getElementById('h5p-bundle-js')) {
      let script = document.createElement('script');
      script.id = 'h5p-bundle-js';
      script.src = 'libs/h5p/main.bundle.js';
      h5pContainer.parentNode.insertBefore(script, h5pContainer.nextSibling);
    }

    window.addEventListener("load", function() {
      const options = {
        h5pJsonPath: h5pJsonPath,
        frameJs: 'libs/h5p/frame.bundle.js',
        frameCss: 'libs/h5p/styles/h5p.css',
      }
      new H5PStandalone.H5P(h5pContainer, options);
    });
  }) ();
</script>

Please pay attention to set variables h5pContainer, h5pJsonPath.
-  h5pContainer can be set as "h5p-container-" + h5p's frame number : h5p-container-8, h5p-container-9 ...
   This should be same as div tag's id attribute.
- h5pJsonPath should be set path of extracted H5P directory following upper instructions.

**All done !**
