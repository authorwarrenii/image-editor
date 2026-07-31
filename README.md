<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Photo Editor</title>
    <script src="https://cloudimg.io"></script>
    <style>
        body, html { margin: 0; padding: 0; width: 100%; height: 100%; overflow: hidden; }
        #editor-container { width: 100vw; height: 100vh; }
    </style>
</head>
<body>

<div id="editor-container"></div>

<script>
    const urlParams = new URLSearchParams(window.location.search);
    let dynamicImage = urlParams.get('img');

    // Cleaned string assignments pointing to an actual valid file asset
    const defaultImage = 'https://cloudimg.io';
    let imageToEdit = dynamicImage ? decodeURIComponent(dynamicImage) : defaultImage;

    // Properly passes the DOM element container first, followed by options object
    const container = document.getElementById('editor-container');
    const filerobotImageEditor = new FilerobotImageEditor(container, {
        source: imageToEdit,
        onSave: (imageObject, imageDesignState) => {
            console.log('Saved Image Data:', imageObject);
            alert('Image saved! Look at your browser console to view output data.');
        },
        onClose: () => {
            alert('Editor closed');
        }
    });

    filerobotImageEditor.render();
</script>

</body>
</html>
