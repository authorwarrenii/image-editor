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
    const urlParams = new URLSearchParams(window.location.search);
    let dynamicImage = urlParams.get('img');

    const defaultImage = 'https://airstore.io';
    let imageToEdit = dynamicImage ? decodeURIComponent(dynamicImage) : defaultImage;

    // IMPORTANT FIX: If it's an ImgBB link, append a timestamp string to force-bypass CORS cache blocks
    if (imageToEdit.includes('ibb.co')) {
        const separator = imageToEdit.includes('?') ? '&' : '?';
        imageToEdit = `${imageToEdit}${separator}not-cached=${new Date().getTime()}`;
    }

    const ImageEditor = new window.FilerobotImageEditor({
        elementId: 'editor-container',
        source: imageToEdit, 
        // Force the editor to process external files correctly
        loadableCanvas: true,
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
