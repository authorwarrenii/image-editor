<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Photo Editor</title>
    <script src="https://scaleflex.it"></script>
    <style>
        body, html { margin: 0; padding: 0; width: 100%; height: 100%; overflow: hidden; }
        #editor-container { width: 100vw; height: 100vh; }
    </style>
</head>
<body>

<div id="editor-container"></div>

<script>
    // 1. Automatically grab the "?img=" parameter from your link URL
    const urlParams = new URLSearchParams(window.location.search);
    const dynamicImage = urlParams.get('img');

    // 2. Set a fallback image in case no image parameter is provided
    const defaultImage = 'https://scaleflex.airstore.io/demo/stephen-walker-unsplash.jpg';
    const imageToEdit = dynamicImage ? decodeURIComponent(dynamicImage) : defaultImage;

    // 3. Initialize the Filerobot Image Editor with the dynamic image
    const ImageEditor = new window.FilerobotImageEditor({
        elementId: 'editor-container',
        source: imageToEdit, 
        onSave: (imageObject, imageDesignState) => {
            console.log('Saved Image Data:', imageObject);
            alert('Image saved successfully!');
        },
        onClose: () => {
            alert('Editor closed');
        }
    });

    ImageEditor.open();
</script>

</body>
</html>
