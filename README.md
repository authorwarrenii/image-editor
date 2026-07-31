<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Photo Editor</title>
    <!-- CORRECTED: Loaded official Filerobot Image Editor CDN -->
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

    // CORRECTED: Pointed fallback directly to a valid sample image file
    const defaultImage = 'https://cloudimg.io';
    let imageToEdit = dynamicImage ? decodeURIComponent(dynamicImage) : defaultImage;

    // Cache-busting logic remains useful for strict CORS configurations
    if (imageToEdit.includes('ibb.co')) {
        const separator = imageToEdit.includes('?') ? '&' : '?';
        imageToEdit = `${imageToEdit}${separator}not-cached=${new Date().getTime()}`;
    }

    // CORRECTED: Updated constructor to match official API definitions
    const filerobotImageEditor = new FilerobotImageEditor(
        document.getElementById('editor-container'),
        {
            source: imageToEdit,
            onSave: (imageObject, imageDesignState) => {
                console.log('Saved Image Data:', imageObject);
                alert('Image saved successfully! Check console for data.');
            },
            onClose: () => {
                alert('Editor closed');
            }
        }
    );

    filerobotImageEditor.render();
</script>

</body>
</html>
