<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Photo Editor</title>
    <!-- Loads Version 4+ Modern Core Bundle -->
    <script src="https://scaleflex.cloudimg.io/v7/plugins/filerobot-image-editor/latest/filerobot-image-editor.min.js"></script>
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

    // Default image that explicitly allows CORS manipulation
    const defaultImage = 'https://cloudimg.io';
    let imageToEdit = dynamicImage ? decodeURIComponent(dynamicImage) : defaultImage;

    // Correct instantiation format for Scaleflex Filerobot v4+
    const filerobotImageEditor = new FilerobotImageEditor(
        document.getElementById('editor-container'),
        {
            source: imageToEdit,
            // Instructs the underlying canvas pipeline to send anonymous CORS requests
            forceToCanvas: true,
            onSave: (imageObject, imageDesignState) => {
                console.log('Saved Image Data:', imageObject);
                alert('Image processed successfully!');
            },
            onClose: () => {
                alert('Editor closed');
            }
        }
    );

    // Replaced the broken .open() call with the modern rendering pipeline
    filerobotImageEditor.render();
</script>

</body>
</html>
