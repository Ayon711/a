html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Free online tool to round corners of your images with transparent background. Smooth Comer helps you create rounded corner images easily with adjustable radius.">
    <meta name="keywords" content="round image corners, transparent background, image editor, online tool, smooth comer, photo editing, corner radius">
    <title>Smooth Comer - Round Image Corners Online</title>
    <style>
        :root {
            --primary: #833ab4;
            --secondary: #fd1d1d;
            --tertiary: #fcb045;
            --light: #f8f9fa;
            --dark: #212529;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            min-height: 100vh;
            color: var(--dark);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px 0;
            background: linear-gradient(to right, var(--primary), var(--secondary), var(--tertiary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            position: relative;
        }

        header::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(to right, var(--primary), var(--secondary), var(--tertiary));
            border-radius: 2px;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            animation: fadeIn 1s ease-in-out;
        }

        .tagline {
            font-size: 1.2rem;
            opacity: 0.8;
            margin-bottom: 20px;
            animation: fadeIn 1.5s ease-in-out;
        }

        .main-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 30px;
        }

        .tool-container {
            background-color: white;
            border-radius: 15px;
            box-shadow: var(--shadow);
            padding: 30px;
            width: 100%;
            max-width: 800px;
            transition: transform 0.3s ease;
        }

        .tool-container:hover {
            transform: translateY(-5px);
        }

        .upload-section {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
            margin-bottom: 30px;
        }

        .drop-area {
            border: 3px dashed #ddd;
            border-radius: 10px;
            width: 100%;
            padding: 40px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
            background-color: #f8f9fa;
        }

        .drop-area:hover {
            border-color: var(--primary);
            background-color: #f0f2f5;
        }

        .drop-area.highlight {
            border-color: var(--tertiary);
            background-color: rgba(252, 176, 69, 0.1);
        }

        .file-input {
            display: none;
        }

        .btn {
            background: linear-gradient(to right, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(131, 58, 180, 0.3);
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(131, 58, 180, 0.4);
        }

        .btn:active {
            transform: translateY(0);
        }

        .btn-secondary {
            background: white;
            color: var(--primary);
            border: 2px solid var(--primary);
            box-shadow: none;
        }

        .btn-secondary:hover {
            background: rgba(131, 58, 180, 0.1);
            box-shadow: none;
        }

        .controls {
            display: flex;
            flex-direction: column;
            gap: 20px;
            width: 100%;
        }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        label {
            font-weight: 600;
            color: var(--dark);
        }

        .slider-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .slider {
            flex-grow: 1;
            -webkit-appearance: none;
            height: 8px;
            border-radius: 4px;
            background: #ddd;
            outline: none;
        }

        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            cursor: pointer;
            transition: all 0.2s;
        }

        .slider::-webkit-slider-thumb:hover {
            transform: scale(1.1);
        }

        .slider-value {
            min-width: 40px;
            text-align: center;
            font-weight: 600;
            color: var(--primary);
        }

        .preview-section {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
            margin-top: 30px;
        }

        .preview-container {
            position: relative;
            width: 100%;
            max-width: 500px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 200px;
            background-color: #f0f2f5;
            border-radius: 10px;
            padding: 20px;
        }

        #previewImage {
            max-width: 100%;
            max-height: 400px;
            display: none;
            border-radius: 0;
            box-shadow: var(--shadow);
        }

        .download-btn {
            display: none;
            margin-top: 20px;
        }

        .loading {
            display: none;
            text-align: center;
            padding: 20px;
        }

        .spinner {
            width: 40px;
            height: 40px;
            border: 4px solid rgba(131, 58, 180, 0.2);
            border-top: 4px solid var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }

        .placeholder-text {
            color: #666;
            text-align: center;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .tagline {
                font-size: 1rem;
            }
            
            .tool-container {
                padding: 20px;
            }
            
            .btn {
                padding: 10px 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Smooth Comer</h1>
            <p class="tagline">Round image corners with transparent background</p>
        </header>

        <div class="main-content">
            <div class="tool-container">
                <div class="upload-section">
                    <div id="dropArea" class="drop-area">
                        <p>Drag & drop your image here or</p>
                        <button id="uploadBtn" class="btn">
                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
                                <path d="M.5 9.9a.5.5 0 0 1 .5.5v2.5a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1v-2.5a.5.5 0 0 1 1 0v2.5a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2v-2.5a.5.5 0 0 1 .5-.5z"/>
                                <path d="M7.646 1.146a.5.5 0 0 1 .708 0l3 3a.5.5 0 0 1-.708.708L8.5 2.707V11.5a.5.5 0 0 1-1 0V2.707L5.354 4.854a.5.5 0 1 1-.708-.708l3-3z"/>
                            </svg>
                            Select Image
                        </button>
                        <input type="file" id="fileInput" class="file-input" accept="image/*">
                    </div>
                </div>

                <div class="controls">
                    <div class="control-group">
                        <label for="cornerRadius">Corner Radius: <span id="radiusValue" class="slider-value">20</span>px</label>
                        <div class="slider-container">
                            <input type="range" id="cornerRadius" class="slider" min="0" max="150" value="20">
                        </div>
                    </div>
                </div>

                <div class="preview-section">
                    <div class="preview-container">
                        <p id="placeholderText" class="placeholder-text">Your rounded image will appear here</p>
                        <img id="previewImage" alt="Preview of your image with rounded corners">
                    </div>

                    <div id="loading" class="loading">
                        <div class="spinner"></div>
                        <p>Processing your image...</p>
                    </div>

                    <button id="downloadBtn" class="btn download-btn">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
                            <path d="M.5 9.9a.5.5 0 0 1 .5.5v2.5a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1v-2.5a.5.5 0 0 1 1 0v2.5a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2v-2.5a.5.5 0 0 1 .5-.5z"/>
                            <path d="M7.646 1.146a.5.5 0 0 1 .708 0l3 3a.5.5 0 0 1-.708.708L8.5 2.707V11.5a.5.5 0 0 1-1 0V2.707L5.354 4.854a.5.5 0 1 1-.708-.708l3-3z"/>
                        </svg>
                        Download PNG (Transparent Background)
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // DOM elements
            const fileInput = document.getElementById('fileInput');
            const uploadBtn = document.getElementById('uploadBtn');
            const dropArea = document.getElementById('dropArea');
            const cornerRadius = document.getElementById('cornerRadius');
            const radiusValue = document.getElementById('radiusValue');
            const previewImage = document.getElementById('previewImage');
            const downloadBtn = document.getElementById('downloadBtn');
            const loading = document.getElementById('loading');
            const placeholderText = document.getElementById('placeholderText');
            const previewContainer = document.querySelector('.preview-container');

            // Current image data
            let currentImage = null;
            let currentImageDataUrl = null;

            // Event listeners
            uploadBtn.addEventListener('click', () => fileInput.click());
            fileInput.addEventListener('change', handleFileSelect);
            dropArea.addEventListener('dragover', handleDragOver);
            dropArea.addEventListener('dragleave', handleDragLeave);
            dropArea.addEventListener('drop', handleDrop);
            cornerRadius.addEventListener('input', updateImage);
            downloadBtn.addEventListener('click', downloadImage);

            // Update slider value display
            cornerRadius.addEventListener('input', function() {
                radiusValue.textContent = this.value;
                updateImage();
            });

            // Handle file selection
            function handleFileSelect(e) {
                const file = e.target.files[0];
                if (file && file.type.match('image.*')) {
                    processImage(file);
                }
            }

            // Handle drag over
            function handleDragOver(e) {
                e.preventDefault();
                e.stopPropagation();
                dropArea.classList.add('highlight');
            }

            // Handle drag leave
            function handleDragLeave(e) {
                e.preventDefault();
                e.stopPropagation();
                dropArea.classList.remove('highlight');
            }

            // Handle drop
            function handleDrop(e) {
                e.preventDefault();
                e.stopPropagation();
                dropArea.classList.remove('highlight');

                const file = e.dataTransfer.files[0];
                if (file && file.type.match('image.*')) {
                    processImage(file);
                }
            }

            // Process the image
            function processImage(file) {
                loading.style.display = 'block';
                previewImage.style.display = 'none';
                downloadBtn.style.display = 'none';
                placeholderText.style.display = 'none';

                const reader = new FileReader();
                reader.onload = function(e) {
                    currentImage = new Image();
                    currentImage.onload = function() {
                        loading.style.display = 'none';
                        previewImage.style.display = 'block';
                        updateImage();
                    };
                    currentImage.src = e.target.result;
                };
                reader.readAsDataURL(file);
            }

            // Update the image with rounded corners
            function updateImage() {
                if (!currentImage) return;

                const radius = parseInt(cornerRadius.value);
                
                // Create canvas
                const canvas = document.createElement('canvas');
                const ctx = canvas.getContext('2d');
                
                // Set canvas dimensions
                canvas.width = currentImage.width;
                canvas.height = currentImage.height;
                
                // Clear canvas with transparent background
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                
                // Draw rounded rectangle path
                ctx.beginPath();
                ctx.moveTo(radius, 0);
                ctx.lineTo(canvas.width - radius, 0);
                ctx.quadraticCurveTo(canvas.width, 0, canvas.width, radius);
                ctx.lineTo(canvas.width, canvas.height - radius);
                ctx.quadraticCurveTo(canvas.width, canvas.height, canvas.width - radius, canvas.height);
                ctx.lineTo(radius, canvas.height);
                ctx.quadraticCurveTo(0, canvas.height, 0, canvas.height - radius);
                ctx.lineTo(0, radius);
                ctx.quadraticCurveTo(0, 0, radius, 0);
                ctx.closePath();
                
                // Clip to the path
                ctx.clip();
                
                // Draw the image
                ctx.drawImage(currentImage, 0, 0);
                
                // Update preview image
                currentImageDataUrl = canvas.toDataURL('image/png');
                previewImage.src = currentImageDataUrl;
                
                // Show download button
                downloadBtn.style.display = 'block';
            }

            // Download the image
            function downloadImage() {
                if (!currentImageDataUrl) return;

                const link = document.createElement('a');
                link.download = 'rounded-corners-image.png';
                link.href = currentImageDataUrl;
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
            }
        });
    </script>
</body>
</html>
