<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>
SetMyStay</title>
   <link rel="icon" type="image/png" href="building.png">


    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        body { 
            font-family: 'Inter', sans-serif; 
            overflow-x: hidden;
            
        }
        
        .bluechip-gradient { 
            background: linear-gradient(135deg, #2563eb, #1d4ed8); 
        }
        
        .hero-overlay {
            background: linear-gradient(135deg, rgba(37, 99, 235, 0.8), rgba(29, 78, 216, 0.9));
        }
        
        .btn-primary { 
            background: #2563eb; 
            color: white; 
            padding: 0.875rem 2rem; 
            border-radius: 0.75rem; 
            transition: all 0.3s ease; 
            border: none; 
            cursor: pointer; 
            font-weight: 600; 
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            font-size: 1rem;
            text-decoration: none;
        }
        
        .btn-primary:hover { 
            background: #1d4ed8; 
            transform: translateY(-2px);
            box-shadow: 0 10px 25px -5px rgba(37, 99, 235, 0.4);
        }
        .btn-secondary { 
            background: #f8fafc; 
            color: #334155; 
            padding: 0.875rem 2rem; 
            border-radius: 0.75rem; 
            transition: all 0.3s ease; 
            border: 2px solid #e2e8f0; 
            cursor: pointer; 
            font-weight: 600;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }
        
        .btn-secondary:hover { 
            background: #f1f5f9; 
            border-color: #cbd5e1;
            transform: translateY(-1px);
        }/* Pagination controls styling */
        #pagination-controls {
            display: flex;  justify-content: center;
            align-items: center;
            margin-top: 30px;
            gap: 10px; /* Space between buttons and page numbers */
        }
        .pagination-button {
            padding: 10px 20px;  background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s ease;  }
        .pagination-button:hover {
            background-color: #0056b3;  }
        .pagination-button:disabled {
            background-color: #cccccc;  cursor: not-allowed;
        }
        #page-numbers {
            display: flex;  gap: 5px; /* Space between individual page numbers */
        }
        .page-number {
            padding: 8px 12px;  border: 1px solid #ddd;
            border-radius: 5px;
            cursor: pointer;
            display: inline-block;
            background-color: #f0f0f0;
            transition: background-color 0.3s ease, color 0.3s ease;  font-size: 0.9rem;
        }
        .page-number:hover {
            background-color: #e0e0e0;  }
        .page-number.active {
            background-color: #0056b3;  color: white;
            font-weight: bold;
            border-color: #0056b3;
        }
 /* Solid Dark Blue Separator Line */
.blue-separator-line {
    border: none;
    height: 2px;
    background-color: #000080; /* A very dark navy blue */
    margin: 20px 0;
    width: 100%;
}

/* Darker Blue Gradient Separator Line */
.blue-gradient-separator {
    border: none;
    height: 2px;
    background: linear-gradient(90deg, #021a50, #032060); /* Darker shades of blue for the gradient */
    margin: 20px 0;
    width: 100%;
}

/* Styling for the navigation bar's active indicator (the "bar") */
.nav-link {
    cursor: pointer;
    padding: 10px 15px; /* Adjust padding to give space for the underline */
    text-decoration: none;
    color: #6b7280; /* Default text color (gray) */
    transition: all 0.3s ease; /* Smooth transition for hover and active states */
    display: inline-block; /* Essential to allow padding and border to work correctly */
    border-bottom: 2px solid transparent; /* Start with a transparent border */
}

/* Styling when hovering over a navigation link */
.nav-link:hover {
    color: #0766ec; /* Darker blue on hover */
    border-bottom: 2px solid #0766ec; /* Show a blue border on hover */
}

/* Styling for the currently active navigation link and its "bar" */
.nav-link.active {
    color: #2563eb; /* Blue text for the active link */
    font-weight: 600; /* Bolder text for active link */
    border-bottom: 2px solid #2563eb; /* The solid blue bar for the active link */
}
.permanent-blue-line {
    /* Replicates the gradient background of the active nav-link underline */
    background: linear-gradient(90deg, #2563eb, #3b82f6); /* bluechip.docx , New Microsoft Word Document (2).docx */
    height: 3px; /* Sets the height of the line */
    border-radius: 2px; /* Adds slight rounding to the corners */
    width: 100%; /* Ensures the line spans the full width of its parent */
    display: block; /* Makes sure the element behaves like a block-level element */
    margin-top: 5px; /* Adds a small margin above the line for spacing */
    
}

        .property-card {
            transition: all 0.3s ease;
            border: 2px solid transparent;
            cursor: pointer;
        }
        
        .property-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            border-color: #e2e8f0;
        }
        .modal { 
            display: none; 
            position: fixed; 
            z-index: 1000; 
            left: 0; 
            top: 0; 
            width: 100%; 
            height: 100%; 
            background-color: rgba(0,0,0,0.6); 
            overflow-y: auto;
            padding: 1rem;
            backdrop-filter: blur(4px);
        }
        
        .modal.show { 
            display: flex; 
            align-items: center; 
            justify-content: center; 
        }
        
        .modal-content { 
            background: white; 
            border-radius: 1rem; 
            /* padding: 2rem; REMOVED this, handled by internal divs now */
            padding: 0 2rem 2rem 2rem; /* Adjusted padding-top to 0, keeps side and bottom padding */
            max-width: 500px; 
            width: 100%; 
            max-height: 90vh; 
            overflow-y: auto;
            position: relative;
            animation: slideIn 0.3s ease-out;
        }
        
        
        @keyframes slideIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .page-section {
            display: none;
        }
        .page-section.active {
            display: block;
        }
        .transparent-pricing {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(135deg, #8b5cf6, #7c3aed);
            backdrop-filter: blur(10px);
            z-index: 50;
            padding: 1rem;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
        }
        .pricing-item {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 0.75rem;
            padding: 1rem;
            text-align: center;
            color: white;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        .pricing-item:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }
        .form-input {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 2px solid #e2e8f0;
            border-radius: 0.5rem;
            transition: all 0.3s ease;
            font-size: 1rem;
        }
        .form-input:focus {
            outline: none;
            border-color: #2563eb;
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }
        .form-group {
            margin-bottom: 1.5rem;
        }
        .form-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #374151;
        }
        .checkbox-group {
            display: grid;
            gap: 1rem;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            margin-top: 0.5rem;
        }
        .checkbox-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.75rem;
            border: 2px solid #e2e8f0;
            border-radius: 0.5rem;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        .checkbox-item:hover {
            border-color: #2563eb;
            background-color: #eff6ff;
        }
        .checkbox-item.selected {
            border-color: #2563eb;
            background-color: #eff6ff;
        }
        .radio-group {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            margin-top: 0.5rem;
        }
        .radio-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.75rem 1.5rem;
            border: 2px solid #e2e8f0;
            border-radius: 0.5rem;
            transition: all 0.3s ease;
            cursor: pointer;
            background-color: white;
        }
        .radio-item:hover {
            border-color: #2563eb;
            background-color: #eff6ff;
        }
        .radio-item.selected {
            background-color: #2563eb;
            color: white;
            border-color: #2563eb;
        }
        .floating-contacts {
            position: fixed;
            z-index: 50;
            display: flex;
            flex-direction: column;
            gap: 1rem;
            bottom: 140px;
            right: 20px;
        }
        .floating-btn {
            width: 4rem;
            height: 4rem;
            border-radius: 50%;
            color: white;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
        }
        .floating-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
        }
        .whatsapp-btn {
            background: #25d366;
        }
        .whatsapp-btn:hover {
            background: #128c7e;
        }
        .email-btn {
            background: #ea4335;
        }
        .email-btn:hover {
            background: #d33b2c;
        }
        .btn-social {
            width: 100%;
            padding: 0.75rem 1rem;
            border-radius: 0.5rem;
            border: 2px solid #e2e8f0;
            background: white;
            color: #374151;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.75rem;
            text-decoration: none;
        }
        .btn-social:hover {
            border-color: #cbd5e1;
            background: #f8fafc;
            transform: translateY(-1px);
        }
        .btn-google:hover {
            border-color: #dc2626;
            background: #fef2f2;
        }
        .btn-twitter:hover {
            border-color: #2563eb;
            background: #eff6ff;
        }
        .forgot-password-link {
            color: #2563eb;
            text-decoration: none;
            font-size: 0.875rem;
            transition: color 0.3s ease;
        }
        .forgot-password-link:hover {
            color: #1d4ed8;
            text-decoration: underline;
        }
        /* Virtual Room and Bed Icon Styling */
.virtual-room {
    text-align: center;
    padding-top: 1rem;
    border-top: 1px solid #e5e7eb; /* tailwind's border-gray-200 */
    margin-top: 1rem;
}
.virtual-room-beds {
    display: flex;
    justify-content: center;
    gap: 15px; /* Spacing between bed icons */
    margin-top: 10px;
}
.bed-icon {
    font-size: 2.5rem; /* Larger icon size */
    transition: transform 0.2s ease-in-out;
}
.bed-icon.vacant:hover {
    transform: scale(1.1); /* Slightly enlarge on hover for vacant beds */
}
.bed-icon.vacant {
    color: #22c55e; /* Green for vacant */
    cursor: pointer;
}
.bed-icon.occupied {
    color: #ef4444; /* Red for occupied */
}
        .divider {
            position: relative;
            text-align: center;
            margin: 1.5rem 0;
        }
        .divider::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            height: 1px;
            background: #e2e8f0;
        }
        .divider span {
            background: white;
            padding: 0 1rem;
            color: #6b7280;
            font-size: 0.875rem;
        }
        .footer {
            background: #1f2937;
            color: white;
            padding: 3rem 0 2rem;
            margin-top: 4rem;
        }
        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1rem;
        }
        .footer-section h3 {
            font-weight: 600;
            margin-bottom: 1rem;
            font-size: 1.125rem;
        }
        .footer-section ul {
            list-style: none;
            padding: 0;
        }
        .footer-section ul li {
            margin-bottom: 0.5rem;
        }
        .footer-section ul li a {
            color: #d1d5db;
            text-decoration: none;
            transition: color 0.3s ease;
        }
        .footer-section ul li a:hover {
            color: #3b82f6;
        }
       .footer-bottom {
    /* border-top: 1px solid #374151; */ /* Remove or comment out this line */
    margin-top: 2rem;
    padding-top: 1rem;
    text-align: center;
    color: #9ca3af;
}
        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }
        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 2.5rem;
            height: 2.5rem;
            background: #374151;
            border-radius: 50%;
            color: white;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        .social-links a:hover {
            background: #3b82f6;
            transform: translateY(-2px);
        }
        .blurred-contact-info {
            filter: blur(4px);
            user-select: none;
            pointer-events: none; /* Prevent selection and clicks on blurred text */
            transition: filter 0.3s ease;
        }
        .unlock-overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(37, 99, 235, 0.1), rgba(29, 78, 216, 0.1));
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 0.5rem;
            z-index: 10; /* Ensure it's above blurred content */
        }
        .details-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
            margin: 1rem 0;
        }
        .detail-item {
            background: #f8fafc;
            padding: 1rem;
            border-radius: 0.5rem;
            border: 1px solid #e2e8f0;
        }
        .detail-label {
            font-weight: 600;
            color: #374151;
            margin-bottom: 0.25rem;
            font-size: 0.875rem;
        }
        .detail-value {
            color: #6b7280;
            font-size: 0.875rem;
        }
        /* Media gallery styling */
        .media-gallery {
            position: relative;
            width: 100%;
            height: 350px; /* Fixed height for gallery */
            background-color: #f0f0f0;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            border-radius: 0.75rem;
            margin-bottom: 1.5rem;
        }
        .media-gallery img,
        .media-gallery video {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain; /* Use contain to show full image/video */
            display: none; /* Hidden by default, managed by JS */
        }
        .media-gallery img.active,
        .media-gallery video.active {
            display: block;
        }
        .media-gallery .nav-arrow {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background-color: rgba(0, 0, 0, 0.5);
            color: white;
            padding: 0.75rem 0.5rem;
            border-radius: 0.5rem;
            cursor: pointer;
            z-index: 10;
            font-size: 1.5rem;
            opacity: 0.7;
            transition: opacity 0.2s ease, background-color 0.2s ease;
        }
        .media-gallery .nav-arrow:hover {
            opacity: 1;
            background-color: rgba(0, 0, 0, 0.7);
        }
        .media-gallery .nav-arrow.left {
            left: 1rem;
        }
        .media-gallery .nav-arrow.right {
            right: 1rem;
        }
        .media-gallery .nav-arrow:disabled {
            opacity: 0.3;
            cursor: not-allowed;
            background-color: rgba(0, 0, 0, 0.3);
        }
        .drop-zone {
            border: 2px dashed #cbd5e1;
            border-radius: 0.75rem;
            padding: 2rem;
            text-align: center;
            color: #64748b;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 150px;
        }
        .drop-zone.drag-over {
            background-color: #eff6ff;
            border-color: #2563eb;
        }
        .drop-zone i {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: #94a3b8;
        }
        .preview-container {
            display: flex;
            flex-wrap: wrap;
            gap: 0.75rem;
            margin-top: 1rem;
        }
        .preview-item {
            position: relative;
            width: 80px;
            height: 80px;
            border-radius: 0.5rem;
            overflow: hidden;
            border: 1px solid #e2e8f0;
            flex-shrink: 0;
        }
        .preview-item img, .preview-item video {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .preview-item .remove-btn {
            position: absolute;
            top: 4px;
            right: 4px;
            background-color: rgba(255, 0, 0, 0.7);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.75rem;
            cursor: pointer;
            opacity: 0.8;
        }
        .preview-item .remove-btn:hover {
            opacity: 1;
        }
        /* Loading Overlay Styles */
        .loading-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(255, 255, 255, 0.95); /* Semi-transparent white background */
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 9999; /* Ensure it's on top of everything */
            transition: opacity 0.3s ease; /* Smooth fade out */
        }
        .loading-overlay.hidden {
            opacity: 0;
            pointer-events: none; /* Allow clicks through once hidden */
        }
        .loading-spinner {
            font-size: 4rem; /* Size of the hammer icon */
            color: #2563eb; /* Blue color for the hammer */
            animation: spin 2s linear infinite; /* Spin animation */
            margin-bottom: 1rem;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .loading-text {
            font-size: 1.25rem;
            color: #374151;
            font-weight: 500;
        }
        /* Sticky modal header for close button */
        .modal-sticky-header {
            position: sticky;
            top: 0;
            background-color: white; /* Ensure background covers scrolling content */
            z-index: 10; /* Ensure it stays above other modal content */
            padding: 2rem 2rem 1rem 2rem; /* Top, right, bottom, left padding for the header itself */
            margin: 0 -2rem; /* Negative margins to extend to edges of content area */
            border-top-left-radius: 1rem;
            border-top-right-radius: 1rem;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05); /* Subtle shadow to show it's above */
            display: flex; /* Added for justify-between and items-center */
            justify-content: space-between;
            align-items: center;
        }
        /* Pricing Plan Cards for paymentModal */
        .pricing-plans-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1.5rem;
        }
        @media (min-width: 640px) { /* Small screens and up */
            .pricing-plans-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        .pricing-card {
            background-color: #f8fafc;
            border: 2px solid #e2e8f0;
            border-radius: 1rem;
            padding: 1.5rem;
            text-align: center;
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
        }
        .pricing-card:hover {
            border-color: #2563eb;
            box-shadow: 0 10px 20px rgba(0,0,0,0.08);
            transform: translateY(-5px);
        }
        .pricing-card-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: #1a202c;
            margin-bottom: 0.5rem;
        }
        .pricing-card-price {
            font-size: 3rem;
            font-weight: 800;
            color: #2563eb;
            margin-bottom: 1rem;
        }
        .pricing-card-price small {
            font-size: 1rem;
            font-weight: 500;
            color: #4a5568;
        }
        .pricing-card-features {
            text-align: left;
            margin-top: 1rem;
            margin-bottom: 1.5rem;
            flex-grow: 1; /* Allows it to expand and push button to bottom */
        }
        .pricing-card-features li {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: #4a5568;
            font-size: 0.9rem;
            margin-bottom: 0.5rem;
        }
        .pricing-card .btn-primary {
            width: 100%;
            padding: 0.75rem;
            font-size: 1rem;
        }
        /* Style for range sliders */
        input[type="range"] {
            -webkit-appearance: none;
            width: 100%;
            height: 8px;
            background: #e2e8f0;
            outline: none;
            border-radius: 5px;
            transition: opacity .2s;
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 20px;
            height: 20px;
            background: #2563eb;
            cursor: pointer;
            border-radius: 50%;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
            transition: background .2s, transform .2s;
        }
        input[type="range"]::-moz-range-thumb {
            width: 20px;
            height: 20px;
            background: #2563eb;
            cursor: pointer;
            border-radius: 50%;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
            transition: background .2s, transform .2s;
        }
        input[type="range"]::-webkit-slider-thumb:hover,
        input[type="range"]::-moz-range-thumb:hover {
            background: #1d4ed8;
            transform: scale(1.1);
        }
        
    </style>
</head>

    

    <script>
        
    // Helper function: Gives a random number of beds (between 1 and 4)
    function getRandomBedCount() {
        return Math.floor(Math.random() * 4) + 1;
    }

    // Helper function: Randomly decides if a bed is occupied (50/50 chance)
    function isBedOccupied() {
        return Math.random() < 0.5;
    }

    // Main function: Creates and displays the virtual beds with icons
    function renderVirtualBeds(containerId) {
        // Selects all listing cards (PGs or Roommates) within the given container
        const containers = document.querySelectorAll(`#${containerId} .property-card, #${containerId} .roommate-card`);
        containers.forEach(card => {
            // Find or create the 'virtual-room' section inside each card
            let virtualRoomDiv = card.querySelector('.virtual-room');
            if (!virtualRoomDiv) { // If it doesn't exist, create it
                virtualRoomDiv = document.createElement('div');
                virtualRoomDiv.className = 'virtual-room';
                card.appendChild(virtualRoomDiv);
            }

            // Set up the internal HTML for the virtual room (title + bed container)
            virtualRoomDiv.innerHTML = '<h4 class="text-md font-semibold text-gray-800 mb-2">Virtual Room Layout:</h4><div class="virtual-room-beds"></div>';
            const bedsContainer = virtualRoomDiv.querySelector('.virtual-room-beds');
            const bedCount = getRandomBedCount(); // Get random number of beds (max 4)

            // Loop to create each bed icon
            for (let i = 0; i < bedCount; i++) {
                const bedIcon = document.createElement('i');
                bedIcon.className = 'fas fa-bed bed-icon'; // Add Font Awesome bed icon class
                if (isBedOccupied()) {
                    bedIcon.classList.add('occupied'); // Make it red if occupied
                    // Occupied beds are not clickable
                } else {
                    bedIcon.classList.add('vacant'); // Make it green if vacant
                    // When a vacant bed is clicked, open the booking modal
                    bedIcon.onclick = () => openBedBookingModal(card.dataset.id || 'N/A', i + 1);
                }
                bedsContainer.appendChild(bedIcon); // Add the bed icon to the container
            }
        });
        
    }

    // Function: Opens the bed booking pop-up modal
    window.openBedBookingModal = function(listingId, bedNumber) {
        document.getElementById('bedBookingListingId').value = listingId; // Store listing ID
        document.getElementById('bedBookingBedNumber').value = bedNumber;   // Store bed number
        document.getElementById('bedBookingModal').classList.add('show');  // Show the modal
    };

    // Function: Closes the bed booking pop-up modal
    window.closeBedBookingModal = function() {
        document.getElementById('bedBookingModal').classList.remove('show'); // Hide the modal
    };

    // Function: Handles the submission of the bed booking form
    window.submitBedBooking = function(event) {
        event.preventDefault(); // Stop the form from reloading the page
        // Get all the input values from the form
        const listingId = document.getElementById('bedBookingListingId').value;
        const bedNumber = document.getElementById('bedBookingBedNumber').value;
        const name = document.getElementById('bedBookingName').value;
        const email = document.getElementById('bedBookingEmail').value;
        const phone = document.getElementById('bedBookingPhone').value;
        const startDate = document.getElementById('bedBookingStartDate').value;
        const endDate = document.getElementById('bedBookingEndDate').value;
        const description = document.getElementById('bedBookingDescription').value;

        // Display booking details in the console (for testing/simulation)
        console.log(`Bed Booking Request for Listing ID: ${listingId}, Bed No: ${bedNumber}`);
        console.log(`Name: ${name}, Email: ${email}, Phone: ${phone}`);
        console.log(`Dates: ${startDate} to ${endDate}`);
        console.log(`Description: ${description}`);

        // Show a success message to the user
        window.showMessageBox('Booking Request Sent', `Your request for Bed ${bedNumber} in Listing ${listingId} has been sent. We will contact you soon.`, 'success');
        window.closeBedBookingModal(); // Close the modal
        // In a real application, you would send this data to your server here
    };
</script>

    <!-- Loading Overlay -->
    <div id="loadingOverlay" class="loading-overlay">
        <i class="fas fa-hammer loading-spinner"></i>
        <p class="loading-text">Loading SetMyStay...</p>
    </div>
    <!-- Header -->
    <header class="bg-white shadow-lg sticky top-0 z-40 backdrop-blur-md bg-white/95">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-18">
                <div class="flex items-center space-x-4 cursor-pointer py-2" onclick="window.showPage('home')">
                    <div class="w-12 h-12 bluechip-gradient rounded-xl flex items-center justify-center shadow-lg">
                        <i class="fas fa-building text-white text-xl"></i>
                    </div>
                    <div>
                        <h1 class="text-2xl font-bold text-gray-900">SetMyStay</h1>
                        <p class="text-sm text-gray-500 font-medium"></p>
                    </div>
                </div>
                
                <!-- Mobile Menu Button -->
                <button class="md:hidden p-3 rounded-lg hover:bg-gray-100 transition-colors" onclick="window.toggleMobileMenu()">
                    <i id="menuIcon" class="fas fa-bars text-gray-700 text-xl"></i>
                </button>
                
                <!-- Desktop Navigation -->
                <nav class="hidden md:flex items-center space-x-8">
                    
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600 active" onclick="window.showPage('home')" data-page="home">Home</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('pg')" data-page="pg">PG Listings</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('rentals')" data-page="rentals">Rentals</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('roommates')" data-page="roommates">Roommates</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('list')" data-page="list">List Property</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600 hidden" id="yourPropertiesNavLink" onclick="window.showPage('your-properties')" data-page="your-properties">Your Properties</a>
                    
                    <!-- Sign In Button -->
                    <button onclick="window.openSignInModal()" class="btn-primary ml-4">
                        <i class="fas fa-user mr-2"></i>
                        Sign In
                    </button>
                   
    </div>
</nav>
                </nav>
            </div>
            
            <!-- Mobile Navigation -->
            <div id="mobileMenu" class="md:hidden hidden bg-white border-t border-gray-200">
                <div class="px-4 py-4 space-y-3">
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('home'); window.toggleMobileMenu()">Home</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('roommates'); window.toggleMobileMenu()">Roommates</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('rentals'); window.toggleMobileMenu()">Rentals</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('pg'); window.toggleMobileMenu()">PG Listings</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="window.showPage('list'); window.toggleMobileMenu()">List Property</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600 hidden" id="yourPropertiesNavLinkMobile" onclick="window.showPage('your-properties'); window.toggleMobileMenu()">Your Properties</a>
                    <button onclick="window.openSignInModal(); window.toggleMobileMenu()" class="btn-primary w-full mt-4">
                        <i class="fas fa-user mr-2"></i>
                        Sign In
                    </button>
                </div>
            </div>
        </div>
    </header>
    <!-- Main Content -->
    <main>
        <!-- Home Page -->
        <div id="home" class="page-section active">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <!-- Hero Section -->
                <div class="relative rounded-2xl overflow-hidden mb-12">
                    <div class="hero-overlay absolute inset-0 z-10"></div>
                    <img 
                        src="https://www.luxuryresidences.in/blog/wp-content/uploads/2024/09/bandra-kurla-complex.jpg" 
                        alt="Modern city skyline" 
                        class="w-full h-96 object-cover" 
                    />
                    
                    <div class="absolute inset-0 z-20 flex items-center justify-center text-center text-white">
                        <div class="max-w-4xl px-6">
                            <h2 class="text-5xl md:text-6xl font-bold mb-6">Find Your Perfect Living Space</h2>
                            <p class="text-xl md:text-2xl mb-8 text-gray-100">
                                Discover roommates, rental properties, and PG accommodations with transparent pricing
                            </p>
                            <div class="flex flex-col sm:flex-row gap-4 justify-center">
                                <button onclick="window.showPage('roommates')" class="btn-primary text-lg px-8 py-4">
                                    <i class="fas fa-users mr-2"></i>
                                    Find Roommates
                                </button>
                                <button onclick="window.showPage('rentals')" class="btn-secondary text-lg px-8 py-4 bg-white/20 border-white/30 text-white hover:bg-white/30 hover:text-white">
                                    <i class="fas fa-home mr-2"></i>
                                    Browse Rentals
                                </button>
                              <button onclick="window.showPage('pg')" class="btn-secondary">
                                <i class="fas fa-building" style="margin-right: 0.5rem;"></i>
                                Browse Co-living / PG
                            </button>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- Features Section -->
                <div class="grid md:grid-cols-3 gap-8 mb-12">
                    <div class="bg-white rounded-xl p-8 shadow-lg hover:shadow-xl transition-shadow">
                        <div class="w-16 h-16 bluechip-gradient rounded-xl flex items-center justify-center mb-6">
                            <i class="fas fa-users text-white text-2xl"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-4">PG Accommodations</h3>
                        <p class="text-gray-600 leading-relaxed">Discover comfortable paying guest accommodations with modern amenities and flexible lease terms.</p>
                        
                    </div>
                    <div class="bg-white rounded-xl p-8 shadow-lg hover:shadow-xl transition-shadow">
                        <div class="w-16 h-16 bluechip-gradient rounded-xl flex items-center justify-center mb-6">
                            <i class="fas fa-home text-white text-2xl"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-4">Premium Rentals</h3>
                        <p class="text-gray-600 leading-relaxed">Explore verified rental properties with detailed amenities, photos, and transparent pricing information.</p>
                    </div>
                    <div class="bg-white rounded-xl p-8 shadow-lg hover:shadow-xl transition-shadow">
                        <div class="w-16 h-16 bluechip-gradient rounded-xl flex items-center justify-center mb-6">
                            <i class="fas fa-bed text-white text-2xl"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-4">Find Roommates</h3>
                        <p class="text-gray-600 leading-relaxed">Connect with compatible roommates based on lifestyle preferences, location, and budget requirements.</p>
                    </div>
                </div>
               <!-- Sample Properties Section -->
                <div class="mb-12">
                    <h3 class="text-3xl font-bold text-gray-900 mb-8 text-center">Featured Properties</h3>
                    <div id="home-featured-properties" class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                        <!-- Featured properties will be loaded here dynamically from Firestore -->
                    </div>
                </div>
                <!-- Sample Roommates Section -->
                <div class="mb-12">
                    <h3 class="text-3xl font-bold text-gray-900 mb-8 text-center">Featured Roommate Profiles</h3>
                    <div id="home-featured-roommates" class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                        <!-- Featured roommates will be loaded here dynamically from Firestore -->
                    </div>
                </div>
            </div>
        </div>
      <div id="roommates" class="page-section">
    <div style="display: flex; flex-direction: column; align-items: center;">
        <h2 class="text-4xl font-bold text-gray-900 mb-8 text-center">Find Your Perfect Roommate</h2>
        <p class="text-xl text-gray-600 text-center mb-8 max-w-3xl">
            Connect with like-minded individuals looking for shared accommodation. Filter by preferences, location, and budget.
        </p>

        <div class="flex flex-col md:flex-row gap-8">
            <div class="md:w-1/3 lg:w-1/4">
                <div class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl border border-gray-100 p-6 mb-8 backdrop-blur-sm flex flex-col gap-6">
                    <div class="flex items-center gap-3">
                        <div class="w-8 h-8 bg-gradient-to-r from-blue-500 to-purple-600 rounded-lg flex items-center justify-center">
                            <svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 4a1 1 0 011-1h16a1 1 0 011 1v2.586a1 1 0 01-.293.707l-6.414 6.414a1 1 0 00-.293.707V17l-4 4v-6.586a1 1 0 00-.293-.707L3.293 7.293A1 1 0 013 6.586V4z"></path>
                            </svg>
                        </div>
                        <h3 class="text-2xl font-bold bg-gradient-to-r from-gray-800 to-gray-600 bg-clip-text text-transparent text-left">
                            Find Your Perfect Match
                        </h3>
                    </div>

                    <div class="form-group">
                        <label class="block text-sm font-semibold text-gray-700 mb-2">Flatmate Type</label>
                        <div class="flex flex-col space-y-2">
                            <button id="wantFlatmateBtn" class="btn-primary px-8 py-3 text-lg" onclick="window.selectFlatmateType('want')">
                                <i class="fas fa-user-friends mr-2"></i> Want to be Flatmate
                            </button>
                            <button id="needFlatmateBtn" class="btn-secondary px-8 py-3 text-lg" onclick="window.selectFlatmateType('need')">
                                <i class="fas fa-house-user mr-2"></i> Need Flatmate
                            </button>
                        </div>
                    </div>

                    <div class="form-group relative">
                        <label class="block text-sm font-semibold text-gray-700 mb-2"> <i class="fas fa-map-marker-alt"></i> Location </label>
                        <input type="text" placeholder="Type city or locality" class="form-input" id="roommate-filter-location-input" autocomplete="off" oninput="window.showLocationSuggestions(this.value)" />
                        <ul id="locationSuggestionsList" class="absolute z-10 w-full bg-white border border-gray-300 rounded-lg shadow-lg mt-1 max-h-60 overflow-y-auto hidden"></ul>
                    </div>

                    <div class="form-group">
                        <label class="block text-sm font-semibold text-gray-700 mb-2">
                            <i class="fas fa-wallet"></i> Budget Range (₹)
                            <span id="roommate-budget-output" class="font-normal text-sm text-gray-500 ml-2">Up to ₹70,000</span>
                        </label>
                        <input type="range" id="roommate-budget-slider" min="2000" max="70000" step="1000" value="70000" class="w-full" oninput="window.updateBudgetOutput('roommate')">
                    </div>

                    <div class="form-group">
                        <label class="block text-sm font-semibold text-gray-700 mb-2">
                            <i class="fas fa-venus-mars"></i> Gender
                        </label>
                        <div class="relative">
                            <select id="roommate-filter-gender" onchange="window.toggleOtherGenderInput()"
                                class="w-full px-4 py-3 bg-white border-2 border-gray-200 rounded-xl focus:border-purple-500 focus:ring-4 focus:ring-purple-100 transition-all duration-200 appearance-none cursor-pointer hover:border-gray-300 shadow-sm">
                                <option value="" disabled selected hidden>Select Gender</option>
                                <option value="Male">Male</option>
                                <option value="Female">Female</option>
                                <option value="Other">Other</option>
                            </select>
                            <div class="absolute inset-y-0 right-0 flex items-center px-3 pointer-events-none">
                                <svg class="w-4 h-4 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
                                </svg>
                            </div>
                        </div>
                        <div id="other-gender-input" class="mt-4 hidden relative">
                            <input type="text" id="genderCustomInput" placeholder="Please specify"
                                oninput="window.showSuggestions(this.value)"
                                class="w-full px-4 py-3 border-2 border-gray-200 rounded-xl focus:border-purple-500 focus:ring-4 focus:ring-purple-100 transition-all duration-200 shadow-sm" />
                            <ul id="suggestionsList"
                                class="absolute z-10 w-full bg-white border border-gray-200 mt-1 rounded-xl shadow-lg hidden max-h-40 overflow-y-auto">
                            </ul>
                        </div>
                    </div>

                    <button class="px-6 py-2 bg-gradient-to-r from-blue-600 to-purple-600 text-white font-semibold rounded-xl hover:from-blue-700 hover:to-purple-700 transform hover:scale-105 transition-all duration-200 shadow-lg hover:shadow-xl" onclick="window.applyRoommateFilters()">
                        Apply Filters
                    </button>

                </div>

            </div>
            <div class="md:w-2/3 lg:w-3/4">
                <div id="roommate-listings" class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    </div>
                <div id="pagination-controls" class="mt-8">
                    <button class="pagination-button" id="prev-page">Previous</button>
                    <div id="page-numbers"></div>
                    <button class="pagination-button" id="next-page">Next</button>
                </div>
            </div>
        </div>
    </div>
</div>
<div id="rentals" class="page-section">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <h2 class="text-4xl font-bold text-gray-900 mb-8 text-left">Premium Rental Properties in Navi Mumbai</h2>
        <p class="text-xl text-gray-600 text-left mb-8 max-w-3xl">
            Discover verified rental properties in Navi Mumbai with complete amenities information and transparent pricing.
        </p>
        <div class="flex flex-col md:flex-row gap-8">
            <div class="md:w-1/3 lg:w-1/4">
                <div class="bg-white rounded-xl shadow-lg p-6 mb-8 flex flex-col gap-6">
                    <h3 class="text-xl font-bold text-gray-900 text-left">Filter Properties</h3>

                    <div class="form-group">
                        <label class="form-label">Furnished Status</label>
                        <div id="rental-furnished-filter" class="radio-group flex-col !flex-wrap-0 items-start">
                            <div class="radio-item selected w-full" data-value="any" onclick="window.toggleFurnishedFilter(this, 'any')">
                                <i class="fas fa-home"></i> <span>Any</span>
                            </div>
                            <div class="radio-item w-full" data-value="Furnished" onclick="window.toggleFurnishedFilter(this, 'Furnished')">
                                <i class="fas fa-couch"></i> <span>Furnished</span>
                            </div>
                            <div class="radio-item w-full" data-value="Semi-Furnished" onclick="window.toggleFurnishedFilter(this, 'Semi-Furnished')">
                                <i class="fas fa-bed"></i> <span>Semi-Furnished</span>
                            </div>
                            <div class="radio-item w-full" data-value="Unfurnished" onclick="window.toggleFurnishedFilter(this, 'Unfurnished')">
                                <i class="fas fa-chair"></i> <span>Unfurnished</span>
                            </div>
                        </div>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Amenities</label>
                        <div id="rental-amenities-filter" class="checkbox-group !grid-cols-1">
                            <div class="checkbox-item" data-value="AC" onclick="window.toggleAmenityFilter(this, 'AC')">
                                <i class="fas fa-snowflake"></i> <span>Air Conditioning</span>
                            </div>
                            <div class="checkbox-item" data-value="WiFi" onclick="window.toggleAmenityFilter(this, 'WiFi')">
                                <i class="fas fa-wifi"></i> <span>Wi-Fi</span>
                            </div>
                            <div class="checkbox-item" data-value="Parking" onclick="window.toggleAmenityFilter(this, 'Parking')">
                                <i class="fas fa-parking"></i> <span>Parking</span>
                            </div>
                            <div class="checkbox-item" data-value="Gym" onclick="window.toggleAmenityFilter(this, 'Gym')">
                                <i class="fas fa-dumbbell"></i> <span>Gym</span>
                            </div>
                            <div class="checkbox-item" data-value="Pool" onclick="window.toggleAmenityFilter(this, 'Pool')">
                                <i class="fas fa-swimmer"></i> <span>Swimming Pool</span>
                            </div>
                            <div class="checkbox-item" data-value="Elevator" onclick="window.toggleAmenityFilter(this, 'Elevator')">
                                <i class="fas fa-elevator"></i> <span>Elevator</span>
                            </div>
                            <div class="checkbox-item" data-value="Security" onclick="window.toggleAmenityFilter(this, 'Security')">
                                <i class="fas fa-shield-alt"></i> <span>24/7 Security</span>
                            </div>
                            <div class="checkbox-item" data-value="Balcony" onclick="window.toggleAmenityFilter(this, 'Balcony')">
                                <i class="fas fa-chair"></i> <span>Balcony</span>
                            </div>
                            <div class="checkbox-item" data-value="Power Backup" onclick="window.toggleAmenityFilter(this, 'Power Backup')">
                                <i class="fas fa-bolt"></i> <span>Power Backup</span>
                            </div>
                            <div class="checkbox-item" data-value="Garden" onclick="window.toggleAmenityFilter(this, 'Garden')">
                                <i class="fas fa-tree"></i> <span>Garden</span>
                            </div>
                        </div>
                    </div>
                    <div class="form-group">
                        <label class="form-label">City/Region</label>
                        <select class="form-input" id="rental-filter-city" onchange="window.updateLocalityOptions(this.value, 'rental')">
                            </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Locality</label>
                        <select class="form-input" id="rental-filter-locality">
                            <option value="">All Localities</option>
                            </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Property Type</label>
                        <select class="form-input" id="rental-filter-type">
                            <option value="" disabled selected hidden>Select Type</option>
                            <option value="1 BHK">1 BHK</option>
                            <option value="2 BHK">2 BHK</option>
                            <option value="3 BHK">3 BHK</option>
                            <option value="4+ BHK">4+ BHK</option>
                            <option value="Independent House">Independent House</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Budget Range (₹) <span id="rental-budget-output" class="font-normal text-sm text-gray-500 ml-2">Up to ₹400,000</span></label>
                        <input type="range" id="rental-budget-slider" min="5000" max="400000" step="5000" value="400000" class="w-full" oninput="window.updateBudgetOutput('rental')">
                    </div>
                    <button class="btn-primary w-full" onclick="window.applyRentalFilters()">
                        <i class="fas fa-search mr-2"></i>
                        Search
                    </button>
                </div>
            </div>
            <div class="md:w-2/3 lg:w-3/4">
                <div id="rental-listings" class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    </div>
                <div id="pagination-controls" class="mt-8">
                    <button class="pagination-button" id="prev-page">Previous</button>
                    <div id="page-numbers"></div>
                    <button class="pagination-button" id="next-page">Next</button>
                </div>
            </div>
        </div>
    </div>
</div>

<div id="pg" class="page-section">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <h2 class="text-4xl font-bold text-gray-900 mb-8 text-center">PG Accommodations in Navi Mumbai</h2>
        <div style="display: flex; justify-content: center;">
            <p class="text-xl text-gray-600 text-center mb-8 max-w-3xl">
                Find comfortable paying guest accommodations in Navi Mumbai with modern amenities and flexible lease terms.
            </p>
        </div>
        <div class="flex flex-col md:flex-row gap-8">
            <div class="md:w-1/3 lg:w-1/4">
                <div class="bg-white rounded-xl shadow-lg p-6 mb-8 flex flex-col gap-6">
                    <h3 class="text-xl font-bold text-gray-900 text-left">Filter PG Listings</h3>
                    <div class="form-group">
                        <label class="form-label">City/Region</label>
                        <select class="form-input" id="pg-filter-city" onchange="window.updateLocalityOptions(this.value, 'pg')">
                            </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Locality</label>
                        <select class="form-input" id="pg-filter-locality">
                            <option value="">All Localities</option>
                            </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Room Type</label>
                        <select class="form-input" id="pg-filter-room-type">
                            <option value="" disabled selected hidden>Select Type</option>
                            <option value="Single Room">Single Room</option>
                            <option value="Double Sharing">Double Sharing</option>
                            <option value="Triple Sharing">Triple Sharing</option>
                            <option value="Quad Sharing">Quad Sharing</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Budget Range (₹) <span id="pg-budget-output" class="font-normal text-sm text-gray-500 ml-2">Up to ₹70,000</span></label>
                        <input type="range" id="pg-budget-slider" min="2000" max="70000" step="1000" value="70000" class="w-full" oninput="window.updateBudgetOutput('pg')">
                    </div>
                    <button class="btn-primary w-full" onclick="window.applyPGFilters()">
                        <i class="fas fa-search mr-2"></i>
                        Search
                    </button>
                </div>
            </div>
            <div class="md:w-2/3 lg:w-3/4">
                <div id="pg-listings" class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    </div>
                <div id="pagination-controls" class="mt-8">
                    <button class="pagination-button" id="prev-page">Previous</button>
                    <div id="page-numbers"></div>
                    <button class="pagination-button" id="next-page">Next</button>
                </div>
            </div>
        </div>
    </div>
</div>
        
        <!-- List Property Page -->
        <div id="list" class="page-section">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <h2 class="text-4xl font-bold text-gray-900 mb-8 text-center">List Your Property</h2>
                <p class="text-xl text-gray-600 text-center mb-12 max-w-3xl mx-auto">
                    Post your property for rent and connect with verified tenants. No registration required!
                </p>
                <div class="bg-white rounded-xl shadow-lg p-8">
                    <form id="listPropertyForm" onsubmit="window.openListingPaymentModal(event)">
                        <!-- Basic Information -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Property Information</h3>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div class="form-group">
                                    <label class="form-label">Property Title</label>
                                    <input type="text" class="form-input" id="property-title" placeholder="e.g., Spacious 2BHK Apartment" required>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Property Type</label>
                                    <select class="form-input" id="property-type" required onchange="window.togglePropertySpecificFields()">
                                        <option value="" disabled selected hidden>Select Type</option>
                                        <option value="Rental">Rental Property (BHK/House)</option>
                                        <option value="PG">PG/Co-living</option>
                                        <option value="Roommate">Looking for Roommate</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Monthly Rent (₹)</label>
                                    <input type="number" class="form-input" id="monthly-rent" placeholder="25000" required>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Area (sq ft)</label>
                                    <input type="number" class="form-input" id="area-sqft" placeholder="1200">
                                </div>
                            </div>
                        </div>
                        <!-- Media Upload (Simulated with local previews) -->
                        <div class="form-group mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Media Upload (Up to 8 Images, 1 Video)</h3>
                            <div id="drop-zone" class="drop-zone" 
                                ondragover="event.preventDefault(); this.classList.add('drag-over');"
                                ondragleave="this.classList.remove('drag-over');"
                                ondrop="window.handleDrop(event); this.classList.remove('drag-over');">
                                <i class="fas fa-cloud-arrow-up"></i>
                                <p class="text-lg font-semibold mb-2">Drag & Drop your media here</p>
                                <p class="text-sm text-gray-500 mb-4">or</p>
                                <input type="file" id="media-files" class="hidden" accept="image/*,video/*" multiple onchange="window.handleFileSelect(event)">
                                <button type="button" onclick="document.getElementById('media-files').click()" class="btn-secondary px-6 py-2">
                                    <i class="fas fa-folder-open mr-2"></i>
                                    Select Files
                                </button>
                                <p class="text-xs text-gray-400 mt-2">Max 8 images, 1 video.</p>
                            </div>
                            <div id="media-preview-container" class="preview-container">
                                <!-- File previews will be displayed here -->
                            </div>
                             <p class="text-sm text-red-500 mt-2">
                                <strong>Note:</strong> File uploads are simulated for preview only. Actual file storage requires backend integration (e.g., Firebase Storage) which is not available in this environment. Newly listed items will use placeholder images if no direct URL is configured in the underlying logic.
                            </p>
                        </div>
                        <!-- Location -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Location</h3>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div class="form-group">
                                    <label class="form-label">City</label>
                                    <select class="form-input" id="city" required>
                                        <option value="Navi Mumbai" selected>Navi Mumbai</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Area/Locality</label>
                                    <select class="form-input" id="locality" required>
                                        <option value="" disabled selected hidden>Select Locality</option>
                                        <option value="CBD Belapur">CBD Belapur</option>
                                        <option value="Kharghar">Kharghar</option>
                                        <option value="Vashi">Vashi</option>
                                        <option value="Nerul">Nerul</option>
                                        <option value="Koparkhairane">Koparkhairane</option>
                                        <option value="Sanpada">Sanpada</option>
                                        <option value="Kamothe">Kamothe</option>
                                        <option value="Kalamboli">Kalamboli</option>
                                        <option value="Panvel">Panvel</option>
                                        <option value="Airoli">Airoli</option>
                                        <option value="Ghansoli">Ghansoli</option>
                                    </select>
                                </div>
                                <div class="form-group md:col-span-2">
                                    <label class="form-label">Complete Address</label>
                                    <textarea class="form-input" id="complete-address" rows="3" placeholder="Enter complete address with landmarks" required></textarea>
                                </div>
                            </div>
                        </div>
                        <!-- Furnished Status (Only for Rentals/PG) -->
                        <div class="mb-8" id="furnished-status-section">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Furnished Status</h3>
                            <div class="radio-group" id="furnished-status-options">
                                <div class="radio-item" data-value="Furnished" onclick="window.selectFurnishedStatus(this, 'Furnished')">
                                      <i class="fas fa-couch"></i>  <span>Furnished</span>
                                </div>
                                <div class="radio-item" data-value="Semi-Furnished" onclick="window.selectFurnishedStatus(this, 'Semi-Furnished')">
                                      <i class="fas fa-bed"></i>  <span>Semi-Furnished</span>
                                </div>
                                <div class="radio-item" data-value="Unfurnished" onclick="window.selectFurnishedStatus(this, 'Unfurnished')">
                                      <i class="fas fa-chair"></i>   <span>Unfurnished</span>
                                </div>
                            </div>
                        </div>
                        <!-- Amenities (Only for Rentals/PG) -->
                        <div class="mb-8" id="amenities-section">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Available Amenities</h3>
                            <div class="checkbox-group" id="amenity-options">
                                <div class="checkbox-item" data-value="AC" onclick="window.toggleAmenity(this, 'AC')">
                                      <i class="fas fa-snowflake"></i>  <span>Air Conditioning</span>
                                </div>
                                <div class="checkbox-item" data-value="WiFi" onclick="window.toggleAmenity(this, 'WiFi')">
                                      <i class="fas fa-wifi"></i>   <span>Wi-Fi</span>
                                </div>
                                <div class="checkbox-item" data-value="Parking" onclick="window.toggleAmenity(this, 'Parking')">
                                      <i class="fas fa-parking"></i>  <span>Parking</span>
                                </div>
                                <div class="checkbox-item" data-value="Gym" onclick="window.toggleAmenity(this, 'Gym')">
                                      <i class="fas fa-dumbbell"></i>  <span>Gym</span>
                                </div>
                                <div class="checkbox-item" data-value="Pool" onclick="window.toggleAmenity(this, 'Pool')">
                                      <i class="fas fa-swimmer"></i>   <span>Swimming Pool</span>
                                </div>
                                <div class="checkbox-item" data-value="Elevator" onclick="window.toggleAmenity(this, 'Elevator')">
                                      <i class="fas fa-elevator"></i> <span>Elevator</span>
                                </div>
                                <div class="checkbox-item" data-value="Security" onclick="window.toggleAmenity(this, 'Security')">
                                      <i class="fas fa-shield-alt"></i>   <span>24/7 Security</span>
                                </div>
                                <div class="checkbox-item" data-value="Balcony" onclick="window.toggleAmenity(this, 'Balcony')">
                                      <i class="fas fa-chair"></i> <span>Balcony</span>
                                </div>
                                <div class="checkbox-item" data-value="Power Backup" onclick="window.toggleAmenity(this, 'Power Backup')">
                                      <i class="fas fa-bolt"></i>   <span>Power Backup</span>
                                </div>
                                <div class="checkbox-item" data-value="Meals" onclick="window.toggleAmenity(this, 'Meals')">
                                      <i class="fas fa-utensils"></i>  <span>Meals Included</span>
                                </div>
                                <div class="checkbox-item" data-value="Laundry" onclick="window.toggleAmenity(this, 'Laundry')">
                                    <i class="fas fa-washer"></i> <span>Laundry Service</span>
                                </div>
                                <div class="checkbox-item" data-value="Housekeeping" onclick="window.toggleAmenity(this, 'Housekeeping')">
                                    <i class="fas fa-broom"></i> <span>Housekeeping</span>
                                </div>
                                <div class="checkbox-item" data-value="Garden" onclick="window.toggleAmenity(this, 'Garden')">
                                      <i class="fas fa-tree"></i>   <span>Garden</span>
                                </div>
                            </div>
                        </div>
                        <!-- Roommate Specific Fields -->
                        <div class="mb-8" id="roommate-specific-fields" style="display:none;">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Roommate Preferences</h3>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div class="form-group">
                                    <label class="form-label">Your Age</label>
                                    <input type="number" class="form-input" id="roommate-age" placeholder="e.g., 25">
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Your Gender</label>
                                    <select class="form-input" id="roommate-gender">
                                        <option value="" disabled selected hidden>Select Gender</option>
                                        <option value="Male">Male</option>
                                        <option value="Female">Female</option>
                                        <option value="Non-Binary">Non-Binary</option>
                                        <option value="Prefer not to say">Prefer not to say</option>
                                    </select>
                                </div>
                                <div class="form-group md:col-span-2">
                                    <label class="form-label">Your Lifestyle Preferences</label>
                                    <div class="checkbox-group" id="roommate-preferences-options">
                                        <div class="checkbox-item" data-value="Non-Smoker" onclick="window.toggleAmenity(this, 'Non-Smoker')">
                                              <i class="fas fa-smoking-ban"></i>   <span>Non-Smoker</span>
                                        </div>
                                        <div class="checkbox-item" data-value="Vegetarian" onclick="window.toggleAmenity(this, 'Vegetarian')">
                                              <i class="fas fa-leaf"></i>   <span>Vegetarian</span>
                                        </div>
                                        <div class="checkbox-item" data-value="Non-Vegetarian" onclick="window.toggleAmenity(this, 'Non-Vegetarian')">
                                              <i class="fas fa-drumstick-bite"></i>   <span>Non-Vegetarian</span>
                                        </div>
                                        <div class="checkbox-item" data-value="Clean" onclick="window.toggleAmenity(this, 'Clean')">
                                              <i class="fas fa-broom"></i>   <span>Clean</span>
                                        </div>
                                        <div class="checkbox-item" data-value="Drinker" onclick="window.toggleAmenity(this, 'Drinker')">
                                              <i class="fa-drinker"></i>   <span>Drinker</span>
                                        </div>
                                        <div class="checkbox-item" data-value="Pet-Friendly" onclick="window.toggleAmenity(this, 'Pet-Friendly')">
                                              <i class="fas fa-paw"></i>   <span>Pet-Friendly</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- Contact Information -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Contact Information</h3>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div class="form-group">
                                    <label class="form-label">Owner/Lister Name</label>
                                    <input type="text" class="form-input" id="owner-name" placeholder="Your full name" required>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Phone Number</label>
                                    <input type="tel" class="form-input" id="phone-number" placeholder="+91 98765 43210" required>
                                </div>
                                 <div class="mb-8"></div>
                                                                <div class="grid md:grid-cols-2 gap-6">
                                 <div class="form-group">
                                    <label class="form-label">Phone Number</label>
                                    <input type="tel" class="form-input" id="phone-number-optional" placeholder="optional">
                                </div>
                        
                            </div>
                        </div>
                                <div class="form-group md:col-span-2">
                                    <label class="form-label">Email Address (Optional)</label>
                                    <input type="email" class="form-input" id="email-address" placeholder="your.email@example.com">
                                </div>
                            </div>
                        </div>
                        <!-- Additional Details -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Additional Details</h3>
                            <div class="form-group">
                                <label class="form-label">Property/Profile Description</label>
                                <textarea class="form-input" id="description" rows="4" placeholder="Describe your property, nearby landmarks, transportation, or your roommate preferences."></textarea>
                            </div>
                           
                        <button type="submit" class="btn-primary w-full text-lg">
                            <i class="fas fa-plus mr-2"></i>
                            List Property
                        </button>
                    </form>
                </div>
            </div>
        </div>
        <!-- Your Properties Section -->
        <div id="your-properties" class="page-section">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <h2 class="text-4xl font-bold text-gray-900 mb-8 text-center">Your Listed Properties</h2>
                <p class="text-xl text-gray-600 text-center mb-12 max-w-3xl mx-auto">
                    Manage your active listings and see how many people have viewed them.
                </p>
                <div id="your-listings-container" class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- User's listed properties will be displayed here -->
                    <!-- This message will be hidden by JS if listings are found or if sign-in is required -->
                    <p id="no-listings-message" class="col-span-full text-center text-gray-500 hidden">You have not listed any properties yet.</p>
                </div>
            </div>
        </div>
    </main>
    <!-- Floating Contact Buttons -->
    <div class="floating-contacts">
        <button class="floating-btn whatsapp-btn" onclick="window.contactWhatsAppGeneral()" title="WhatsApp Support">
            <i class="fab fa-whatsapp"></i>
        </button>
        <button class="floating-btn email-btn" onclick="window.contactEmailGeneral()" title="Email Support">
            <i class="fas fa-envelope"></i>
        </button>
    </div>
 
    <!-- Footer -->
    <footer class="footer">
        <div class="footer-grid">
            <div class="footer-section">
                <div class="flex items-center space-x-3 mb-4">
                    <div class="w-10 h-10 bluechip-gradient rounded-lg flex items-center justify-center">
                        <i class="fas fa-building text-white"></i>
                    </div>
                    
                    <div>
                        <h3 class="text-xl font-bold">SetMyStay</h3>
                        <p class="text-sm text-gray-400">Premium Solutions</p>
                    </div>
                </div>
                <p class="text-gray-300 mb-4">
                    Your trusted partner for finding the perfect living space. Connecting people with their ideal homes since 2025.
                </p>
                <div class="social-links">
                    <a href="#" title="Facebook"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" title="Twitter"><i class="fab fa-twitter"></i></a>
                    <a href="#" title="Instagram"><i class="fab fa-instagram"></i></a>
                    <a href="#" title="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
                </div>
            </div>
            <div class="footer-section">
                <h3>Services</h3>
                <ul>
                    <li><a href="#" onclick="window.showPage('pg')">PG Accommodations</a></li>
                    <li><a href="#" onclick="window.showPage('rentals')">Rental Properties</a></li>
                    <li><a href="#" onclick="window.showPage('roommates')">Find Roommates</a></li>
                    <li><a href="#" onclick="window.showPage('list')">List Property</a></li>
                    <li><a href="#">Property Management</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul>
                    <li><a href="#" onclick="window.showPage('home')">Home</a></li>
                    <li><a href="#" onclick="window.showPage('your-properties')">Your Properties</a></li>
                    <li><a href="#" onclick="window.openInquiryModal()">Contact Us</a></li>
                    <li><a href="https://g.co/kgs/goQB3YY" target="_blank">Visit Our Office</a></li>
                    <!-- Link to Admin Dashboard -->
                  <!-- Menu Link -->
<ul>
  <li>
    <a href="#" onclick="start3FA()" class="text-black hover:text-blue-600">
      Admin Dashboard (3FA)
    </a>
  </li>
</ul>

<!-- 3FA Modal -->
<div id="modal3FA" class="fixed inset-0 bg-black bg-opacity-50 hidden justify-center items-center z-50">
  <div class="bg-white p-6 rounded-xl w-96 shadow-xl text-center relative">
    
    <!-- Close Button -->
    <button onclick="close3FA()" class="absolute top-2 right-4 text-gray-600 hover:text-red-600 text-xl font-bold">&times;</button>

    <h2 id="3fa-title" class="text-xl font-bold mb-4 text-black">Step 1: Username & Password</h2>

    <!-- Step 1: Username and Password -->
    <input type="text" id="3fa-username" class="step-field w-full border border-gray-300 rounded-lg mb-3 p-2 text-black" placeholder="Enter Username">
    <input type="password" id="3fa-password" class="step-field w-full border border-gray-300 rounded-lg mb-4 p-2 text-black" placeholder="Enter Password">

    <!-- Step 2: PIN -->
    <input type="password" id="3fa-pin" maxlength="4" class="step-field w-full border border-gray-300 rounded-lg mb-4 p-2 hidden text-black" placeholder="Enter 4-digit PIN">

    <!-- Step 3: OTP -->
    <input type="text" id="3fa-otp" maxlength="6" class="step-field w-full border border-gray-300 rounded-lg mb-4 p-2 hidden text-black" placeholder="Enter 6-digit OTP">

    <button onclick="next3FAStage()" class="bg-green-500 text-white px-4 py-2 rounded-lg w-full hover:bg-green-600">
      Next
    </button>
  </div>
</div>

<script>
  let currentStage = 1;

  function start3FA() {
    document.getElementById("modal3FA").classList.remove("hidden");
    document.getElementById("modal3FA").classList.add("flex");
    currentStage = 1;
    updateStage();
  }

  function close3FA() {
    document.getElementById("modal3FA").classList.remove("flex");
    document.getElementById("modal3FA").classList.add("hidden");
  }

  function next3FAStage() {
    if (currentStage < 3) {
      currentStage++;
      updateStage();
    } else {
      complete3FA();
    }
  }


  function updateStage() {
    document.querySelectorAll(".step-field").forEach(el => el.classList.add("hidden"));
    const title = document.getElementById("3fa-title");

    if (currentStage === 1) {
      title.textContent = "Step 1: Username & Password";
      document.getElementById("3fa-username").classList.remove("hidden");
      document.getElementById("3fa-password").classList.remove("hidden");
    } else if (currentStage === 2) {
      title.textContent = "Step 2: Enter PIN";
      document.getElementById("3fa-pin").classList.remove("hidden");
    } else if (currentStage === 3) {
      title.textContent = "Step 3: Enter OTP";
      document.getElementById("3fa-otp").classList.remove("hidden");
      document.querySelector("button.bg-green-500").textContent = "Verify & Enter";
    }
  }

  function complete3FA() {
    window.location.href = "admin.html";
  }
  function displayProperties(page) {
    propertyListings.innerHTML = ''; // Clear existing properties in the container
    const startIndex = (page - 1) * propertiesPerPage;
    const endIndex = startIndex + propertiesPerPage;
    const propertiesToShow = propertiesData.slice(startIndex, endIndex);

    if (propertiesToShow.length === 0) {
        propertyListings.innerHTML = '<p class="text-center text-gray-500">No properties found for this page.</p>';
        return;
    }

    // Modify this forEach loop:
    propertiesToShow.forEach((property, index) => { // <-- Add 'index' as a parameter here
        const propertyDiv = document.createElement('div');
        propertyDiv.classList.add('property-item');
        propertyDiv.innerHTML = `
            <h3>${startIndex + index + 1}. ${property.name}</h3> <p><strong>Type:</strong> ${property.type}</p>
            <p><strong>Location:</strong> ${property.location}</p>
            <p><strong>Price:</strong> ${property.price}</p>
            <p>${property.description}</p>
        `;
        propertyListings.appendChild(propertyDiv);
    });
}

</script>

            </div>
            <div class="footer-section">
                <h3>Support</h3>
                <ul>
                  
                    
                    
                    <li>
                        <p class="text-sm text-gray-300 mt-2">
                            <strong>Address:</strong> Office no. 01, Neelsidhi Splendour, <br>
                            Sector 15, CBD Belapur, Navi Mumbai, <br>
                            Maharashtra 400614
                        </p>
                    </li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2025 SetMyStay. All rights reserved. | Designed with    <i class="fas fa-heart text-red-500"></i>   for better living</p>
        </div>
    </footer>
    <!-- Sign In Modal -->
    <div id="signInModal" class="modal">
        <div class="modal-content">
            <div class="modal-sticky-header">
                <h2 class="text-2xl font-bold text-gray-900">Welcome Back</h2>
                <button onclick="window.closeSignInModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <!-- Social Login Buttons -->
            <div class="space-y-3 mb-6 mt-6"> <!-- Added mt-6 to compensate for sticky header padding -->
                <button class="btn-social btn-google">
                    <i class="fab fa-google text-red-500"></i>
                    <span>Continue with Google</span>
                </button>
<button class="btn-social btn-facebook">
                   <i class="fab fa-facebook-f text-blue-500"></i>
                    <span>Continue with Facebook </span>
                </button>
            </div>
            <div class="divider">
                <span>or sign in with email</span>
            </div>
            <form id="signInForm" onsubmit="window.handleSignIn(event)">
                <div class="form-group">
                    <label class="form-label">Email Address</label>
                    <input type="email" class="form-input" placeholder="Enter your email" required>
                </div>
                
                <div class="form-group">
                    <label class="form-label">Password</label>
                    <input type="password" class="form-input" placeholder="Enter your password" required>
                </div>
                
                <div class="flex items-center justify-between mb-6">
                    <label class="flex items-center">
                        <input type="checkbox" class="mr-2">
                        <span class="text-sm text-gray-600">Remember me</span>
                    </label>
                    <a href="#" onclick="window.openForgotPasswordModal()" class="forgot-password-link">
                        Forgot password?
                    </a>
                </div>
                
                <button type="submit" class="btn-primary w-full">
                    <i class="fas fa-sign-in-alt mr-2"></i>
                    Sign In
                </button>
            </form>
            
            <p class="text-center text-gray-600 mt-6">
                Don't have an account? 
                <a href="#" class="text-blue-600 hover:text-blue-700 font-medium">Sign up here</a>
            </p>
        </div>
    </div>
    <!-- Forgot Password Modal -->
    <div id="forgotPasswordModal" class="modal">
        <div class="modal-content">
            <div class="modal-sticky-header">
                <h2 class="text-2xl font-bold text-gray-900">Reset Password</h2>
                <button onclick="window.closeForgotPasswordModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <form id="forgotPasswordForm" onsubmit="window.handleForgotPassword(event)">
                <div class="form-group mt-6"> <!-- Added mt-6 -->
                    <label class="form-label">Email Address</label>
                    <input type="email" class="form-input" placeholder="Enter your email address" required>
                    <p class="text-sm text-gray-500 mt-2">
                        We'll send you a link to reset your password.
                    </p>
                </div>
                
                <button type="submit" class="btn-primary w-full">
                    <i class="fas fa-envelope mr-2"></i>
                    Send Reset Link
                </button>
            </form>
            
            <div class="text-center mt-6">
                <button onclick="window.backToSignIn()" class="text-blue-600 hover:text-blue-700 font-medium">
                    <i class="fas fa-arrow-left mr-2"></i>
                    Back to Sign In
                </button>
            </div>
        </div>
    </div>
    <!-- Property Details Modal -->
    <div id="propertyDetailsModal" class="modal">
        <div class="modal-content" style="max-width: 800px;">
            <div class="modal-sticky-header">
                <h2 id="propertyDetailsTitle" class="text-2xl font-bold text-gray-900">Property Details</h2>
                <button onclick="window.closePropertyDetailsModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <div id="propertyDetailsContent" class="mt-6"> <!-- Added mt-6 -->
                <!-- Content will be dynamically inserted -->
            </div>
        </div>
    </div>
    <!-- Roommate Details Modal -->
    <div id="roommateDetailsModal" class="modal">
        <div class="modal-content" style="max-width: 800px;">
            <div class="modal-sticky-header">
                <h2 id="roommateDetailsTitle" class="text-2xl font-bold text-gray-900">Roommate Profile</h2>
                <button onclick="window.closeRoommateDetailsModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <div id="roommateDetailsContent" class="mt-6"> <!-- Added mt-6 -->
                <!-- Content will be dynamically inserted -->
            </div>
        </div>
    </div>
    <!-- Payment Modal for Address -->
    <div id="paymentModal" class="modal">
        <div class="modal-content" style="max-width: 600px;">
            <div class="modal-sticky-header">
                <h2 class="text-2xl font-bold text-gray-900">Unlock Details</h2>
                <button onclick="window.closePaymentModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <div class="text-center mb-6 mt-6"> <!-- Added mt-6 -->
                <div class="w-20 h-20 bg-yellow-100 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-lock text-yellow-600 text-2xl"></i>
                </div>
                <h3 class="text-xl font-semibold text-gray-900 mb-2">Choose Your Unlock Plan</h3>
                <p class="text-gray-600">Get access to complete address and contact details for verified listings.</p>
            </div>
            
            <div class="pricing-plans-grid">
                
                <!-- Plan 1: 1 Unlock -->
                <div class="pricing-card">
                    <div class="w-full">
                        <p class="pricing-card-title">Basic Unlock</p>
                        <p class="pricing-card-price">₹49<small>/unlock</small></p>
                        <ul class="pricing-card-features">
                            <li><i class="fas fa-check text-green-500 mr-2"></i>1 Listing Unlock</li>
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Complete Address</li>
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Direct Contact Details</li>
                        </ul>
                    </div>
                    <button onclick="window.processPaymentForDetailsUnlock('single')" class="btn-primary">
                        <i class="fas fa-credit-card mr-2"></i>Buy Now
                    </button>
                </div>
                
                <!-- Plan 2: 5 Unlocks -->
                <div class="pricing-card">
                    <div class="w-full">
                        <p class="pricing-card-title">Value Pack</p>
                        <p class="pricing-card-price">₹199<small>/5 unlocks</small></p>
                        <ul class="pricing-card-features">
                            <li><i class="fas fa-check text-green-500 mr-2"></i>5 Listing Unlocks</li>
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Complete Address</li>
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Direct Contact Details</li>
                            <li><i class="fas fa-star text-yellow-500 mr-2"></i>Best Value!</li>
                        </ul>
                    </div>
                    <button onclick="window.processPaymentForDetailsUnlock('bundle')" class="btn-primary">
                        <i class="fas fa-credit-card mr-2"></i>Buy Now
                    </button>
                </div>

                <!-- NEW Plan: 10 Unlocks -->
                <div class="pricing-card">
                    <div class="w-full">
                        <p class="pricing-card-title">Pro Pack</p>
                        <p class="pricing-card-price">₹399<small>/10 unlocks</small></p>
                        <ul class="pricing-card-features">
                            <li><i class="fas fa-check text-green-500 mr-2"></i>10 Listing Unlocks</li>
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Complete Address</li>
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Direct Contact Details</li>
                            <li><i class="fas fa-certificate text-blue-500 mr-2"></i>Great Deal!</li>
                        </ul>
                    </div>
                    <button onclick="window.processPaymentForDetailsUnlock('bundle-large')" class="btn-primary">
                        <i class="fas fa-credit-card mr-2"></i>Buy Now
                    </button>
                </div>

                <!-- NEW Plan: Unlimited Unlocks -->
                <div class="pricing-card">
                    <div class="w-full">
                        <p class="pricing-card-title">Ultimate Pack</p>
                        <p class="pricing-card-price">₹999<small>/unlimited</small></p>
                        <ul class="pricing-card-features">
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Unlimited Listing Unlocks</li>
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Complete Address</li>
                            <li><i class="fas fa-check text-green-500 mr-2"></i>Direct Contact Details</li>
                            <li><i class="fas fa-crown text-yellow-600 mr-2"></i>Best Value & Freedom!</li>
                        </ul>
                    </div>
                    <button onclick="window.processPaymentForDetailsUnlock('unlimited')" class="btn-primary">
                        <i class="fas fa-credit-card mr-2"></i>Buy Now
                    </button>
                </div>
            </div>
            
            <p class="text-xs text-gray-500 text-center mt-6">
                Secure payment powered by SetMyStay
            </p>
        </div>
    </div>
    
    <!-- NEW: Payment Modal for Listing Property -->
    <div id="listPropertyPaymentModal" class="modal">
        <div class="modal-content" style="max-width: 500px;">
            <div class="modal-sticky-header">
                <h2 class="text-2xl font-bold text-gray-900">List Property</h2>
                <button onclick="window.closeListPropertyPaymentModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <div class="text-center mb-6 mt-6"> <!-- Added mt-6 -->
                <div class="w-20 h-20 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-hand-holding-usd text-blue-600 text-2xl"></i>
                </div>
                <h3 class="text-xl font-semibold text-gray-900 mb-2">One-Time Listing Fee</h3>
                <p class="text-gray-600">A small fee to ensure quality listings and reach more genuine tenants.</p>
            </div>
            <div class="bg-purple-50 rounded-lg p-4 mb-6">
                <div class="flex justify-between items-center">
                    <div>
                        <h4 class="font-semibold text-gray-900">Property Listing</h4>
                        <p class="text-sm text-gray-600">One-time payment for 30-day listing</p>
                    </div>
                    <div class="text-right">
                        <span class="text-2xl font-bold text-purple-600">₹999</span>
                    </div>
                </div>
            </div>
            <div class="space-y-4 mb-6">
                <div class="flex items-center text-sm text-gray-600">
                    <i class="fas fa-check text-green-500 mr-3"></i>
                    <span>Your listing live for 30 days</span>
                </div>
                <div class="flex items-center text-sm text-gray-600">
                    <i class="fas fa-check text-green-500 mr-3"></i>
                    <span>Featured on home page (randomly)</span>
                </div>
                <div class="flex items-center text-sm text-gray-600">
                    <i class="fas fa-check text-green-500 mr-3"></i>
                    <span>Reach thousands of potential tenants</span>
                </div>
            </div>
            <button onclick="window.processPaymentForListing()" class="btn-primary w-full text-lg">
                <i class="fas fa-credit-card mr-2"></i>
                Pay ₹999 & List Property
            </button>
            <p class="text-xs text-gray-500 text-center mt-4">
                Secure payment powered by SetMyStay
            </p>
        </div>
    </div>
    <!-- Inquiry Modal -->
    <div id="inquiryModal" class="modal">
        <div class="modal-content">
            <div class="modal-sticky-header">
                <h2 class="text-2xl font-bold text-gray-900">Inquire About a Listing</h2>
                <button onclick="window.closeInquiryModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            <form id="inquiryForm" onsubmit="event.preventDefault()">
                <div class="form-group mt-6"> <!-- Added mt-6 -->
                    <label class="form-label">Property/Roommate Title (Optional)</label>
                    <input type="text" class="form-input" id="inquiry-property-title" placeholder="e.g., Spacious 2BHK Apartment">
                    <small class="text-gray-500">Mention the listing you are interested in.</small>
                </div>
                 <div class="form-group">
                    <label class="form-label">Your Name</label>
                    <input type="text" class="form-input" id="inquiry-user-name" placeholder="Your Name" required>
                </div>
                <div class="form-group">
                    <label class="form-label">Your Phone Number</label>
                    <input type="tel" class="form-input" id="inquiry-user-phone" placeholder="+91 XXXXXXXXXX" required>
                </div>
                <div class="form-group">
                    <label class="form-label">Your Message (Optional)</label>
                    <textarea class="form-input" id="inquiry-message" rows="3" placeholder="I'm interested in this listing. Can you provide more details?"></textarea>
                </div>
                
                <div class="flex flex-col sm:flex-row gap-4 mt-6">
                    <button type="button" onclick="window.sendInquiryWhatsApp()" class="btn-primary flex-1">
                        <i class="fab fa-whatsapp mr-2"></i>Send via WhatsApp
                    </button>
                    <button type="button" onclick="window.sendInquirySMS()" class="btn-secondary flex-1">
                        <i class="fas fa-sms mr-2"></i>Send via SMS
                    </button>
                </div>
            </form>
        </div>
    </div>
    <!-- Message Box (Instead of alert()) -->
    <div id="messageBox" class="modal">
        <div class="modal-content" style="max-width: 400px; text-align: center;">
            <div class="modal-sticky-header justify-end"> <!-- justify-end to align X right -->
                <button onclick="window.closeMessageBox()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            <div id="messageBoxIcon" class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 mt-6"></div> <!-- Added mt-6 -->
            <h3 id="messageBoxTitle" class="text-xl font-semibold text-gray-900 mb-2"></h3>
            <p id="messageBoxContent" class="text-gray-600 mb-6"></p>
            <button onclick="window.closeMessageBox()" class="btn-primary w-full">OK</button>
        </div>
    </div>
    <!-- Confirmation Dialog -->
    <div id="confirmationModal" class="modal">
        <div class="modal-content" style="max-width: 400px; text-align: center;">
            <div class="modal-sticky-header justify-end"> <!-- justify-end to align X right -->
                <button onclick="window.cancelConfirmation()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            <div id="confirmationIcon" class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 mt-6"> <!-- Added mt-6 -->
                <i class="fas fa-question-circle text-2xl text-blue-600"></i>
            </div>
            <h3 id="confirmationTitle" class="text-xl font-semibold text-gray-900 mb-2">Confirm Action</h3>
            <p id="confirmationMessage" class="text-gray-600 mb-6">Are you sure you want to proceed?</p>
            <div class="flex gap-4">
                <button onclick="window.confirmAction()" class="btn-primary flex-1">Yes</button>
                <button onclick="window.cancelConfirmation()" class="btn-secondary flex-1">No</button>
            </div>
        </div>
    </div>
    <!-- NEW: Promotional Pop-up Modal -->
    <div id="promoModal" class="modal">
        <div class="modal-content" style="max-width: 400px; text-align: center;">
            <div class="modal-sticky-header justify-end">
                <button onclick="window.closePromoModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            <div class="text-center mb-6 mt-6">
                <div class="w-20 h-20 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-bullhorn text-blue-600 text-2xl"></i>
                </div>
                <h3 class="text-xl font-semibold text-gray-900 mb-2">Unlock More Details!</h3>
                <p class="text-gray-600 mb-4">Get direct contact information and full addresses for multiple listings.</p>
                <button onclick="window.openPaymentModal(); window.closePromoModal();" class="btn-primary w-full mb-3">
                    <i class="fas fa-lock-open mr-2"></i>Explore Unlock Plans
                </button>
                <button onclick="window.closePromoModal()" class="btn-secondary w-full">
                    Skip for now
                </button>
            </div>
        </div>
    </div>
    <script type="module">
        // Firebase SDK imports
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, onSnapshot, doc, getDoc, updateDoc, increment } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        
        // Firebase Initialization and Authentication
        let app; // Keeping app local to the module
        window.db; // Made global for direct access from console/HTML event listeners if needed
        window.auth; // Made global
        window.currentUserId = null; // Made global
        window.isAuthReady = false; // Made global
        window.isAnonymousUser = true; // Track if the current user is anonymous
        // App ID and Firebase Config from Canvas environment
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        
        // Data caches for properties and roommates (made global)
        window.allProperties = [];
        window.allRoommates = [];
        window.allPgListings = [];
        
        // Currently viewed item ID (for modals) (made global)
        window.currentViewedItemId = null;
        window.currentViewedItemType = null; // 'property' or 'roommate' or 'pg'
        
        // Variable to track available unlocks (persisted in localStorage)
        window.availableUnlocks = parseInt(localStorage.getItem('bluechipUnlocks')) || 0; // Initialize from localStorage or 0
        window.isUnlimitedUnlocks = localStorage.getItem('bluechipUnlimitedUnlocks') === 'true'; // New flag for unlimited
        
        // Store form data temporarily for listing payment (made global)
        window.tempListingData = {};
        
        // --- Global Contact Number ---
        const BLUECHIP_CONTACT_NUMBER = '+918210552902'; // New contact number
        
        // --- Media Upload State --- (made global)
        window.selectedMediaFiles = [];
        const MAX_IMAGES = 8;
        const MAX_VIDEO = 1;
        // --- Location Suggestions Data ---
        window.locationSuggestionsData = [
            { locality: 'CBD Belapur', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Kharghar', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Vashi', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Nerul', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Koparkhairane', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Sanpada', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Kamothe', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Kalamboli', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Panvel', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Airoli', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Ghansoli', city: 'Navi Mumbai', state: 'Maharashtra' },
            { locality: 'Andheri', city: 'Mumbai', state: 'Maharashtra' },
            { locality: 'Bandra', city: 'Mumbai', state: 'Maharashtra' },
            { locality: 'Dadar', city: 'Mumbai', state: 'Maharashtra' },
            { locality: 'Colaba', city: 'Mumbai', state: 'Maharashtra' },
            { locality: 'Baner', city: 'Pune', state: 'Maharashtra' },
            { locality: 'Kothrud', city: 'Pune', state: 'Maharashtra' },
            { locality: 'Hadapsar', city: 'Pune', state: 'Maharashtra' },
            { locality: 'Koregaon Park', city: 'Pune', state: 'Maharashtra' },
            { locality: 'Koramangala', city: 'Bangalore', state: 'Karnataka' },
            { locality: 'Indiranagar', city: 'Bangalore', state: 'Karnataka' },
            { locality: 'Electronic City', city: 'Bangalore', state: 'Karnataka' },
            { locality: 'Jayanagar', city: 'Bangalore', state: 'Karnataka' },
            { locality: 'Chennai', city: 'Chennai', state: 'Tamil Nadu' },
            { locality: 'Hyderabad', city: 'Hyderabad', state: 'Telangana' },
            { locality: 'Delhi', city: 'Delhi', state: 'Delhi' }
        ];
        window.allGenders = [ // Renamed from genderOptions to allGenders for clarity in main script
            "Male",
            "Female",
            "Lesbian",
            "Gay",
            "Bisexual",
            "Transgender Male",
            "Transgender Female",
            "Non-binary",
            "Genderfluid",
            "Agender",
            "Bigender",
            "Pangender",
            "Genderqueer",
            "Two-spirit",
            "Prefer not to say"
        ];
        // --- EMOJI MAPPINGS (UPDATED TO FONT AWESOME ICONS) ---
        // Amenities icons
        window.amenityEmojis = {
            "AC": "<i class=\"fas fa-snowflake\"></i>",
            "WiFi": "<i class=\"fas fa-wifi\"></i>",
            "Parking": "<i class=\"fas fa-parking\"></i>",
            "Gym": "<i class=\"fas fa-dumbbell\"></i>",
            "Pool": "<i class=\"fas fa-swimmer\"></i>",
            "Elevator": "<i class=\"fas fa-elevator\"></i>",
            "Security": "<i class=\"fas fa-shield-alt\"></i>",
            "Balcony": "<i class=\"fas fa-chair\"></i>", // Using a chair as a simple representation
            "Power Backup": "<i class=\"fas fa-bolt\"></i>",
            "Meals": "<i class=\"fas fa-utensils\"></i>",
            "Laundry": "<i class=\"fas fa-washer\"></i>",
            "Housekeeping": "<i class=\"fas fa-broom\"></i>",
            "Garden": "<i class=\"fas fa-tree\"></i>"
        };
        // Lifestyle preferences icons
        window.lifestyleEmojis = {
            "Non-Smoker": "<i class=\"fas fa-smoking-ban\"></i>",
            "Vegetarian": "<i class=\"fas fa-leaf\"></i>",
            "Non-Vegetarian": "<i class=\"fas fa-drumstick-bite\"></i>",
            "Clean": "<i class=\"fas fa-broom\"></i>",
            "Drinker": "<i class=\"fas fa-beer\"></i>",
            "Pet-Friendly": "<i class=\"fas fa-paw\"></i>"
        };
        // --- Dummy Data (Examples) (made global) ---
        window.dummyProperties = [
            {
                id: 'premium-pg-cbd',
                propertyType: 'PG',
                title: 'Premium PG for Professionals',
                rent: 18000,
                area: 150, // per person assumed space
                city: 'Navi Mumbai',
                locality: 'CBD Belapur',
                state: 'Maharashtra', // Added state
                completeAddress: '101, Elite Residency, Sector 11, CBD Belapur, Navi Mumbai, Maharashtra 400614', // Full address
                partialAddress: 'Sector 11, CBD Belapur, Navi Mumbai',
                ownerName: 'Rohan Mehta',
                contactPhone: '+919911223344',
                contactEmail: 'rohan.m@example.com',
                description: 'A premium PG accommodation offering single rooms with all modern amenities. Ideal for working professionals seeking comfort and convenience in CBD Belapur.',
                furnishedStatus: 'Furnished',
                amenities: ['AC', 'WiFi', 'Meals', 'Laundry', 'Housekeeping', 'Security'],
                size: 'Single Room',
                images: [
                    'https://images.unsplash.com/photo-1586023492125-27b2c045efd7?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300',
                    'https://images.unsplash.com/photo-1588806509938-23212879555e?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
                    'https://images.unsplash.com/photo-1589182352131-dcdd920ef0d2?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 125, // Added views
                ownerId: 'dummyOwner1' // Example ownerId for dummy data
            },
            {
                id: 'luxury-2bhk-vashi',
                propertyType: 'Rental',
                title: 'Luxury 2BHK Apartment',
                rent: 45000,
                area: 1200,
                city: 'Navi Mumbai',
                locality: 'Vashi',
                state: 'Maharashtra', // Added state
                completeAddress: '205, Ocean Breeze, Sector 17, Vashi, Navi Mumbai, Maharashtra 400703', // Full address
                partialAddress: 'Sector 17, Vashi, Navi Mumbai',
                ownerName: 'Smita Patel',
                contactPhone: '+918877665544',
                contactEmail: 'smita.p@example.com',
                description: 'Elegantly designed 2BHK apartment in the heart of Vashi. Features spacious rooms, modern kitchen, and access to all city conveniences.',
                furnishedStatus: 'Furnished',
                amenities: ['AC', 'WiFi', 'Parking', 'Gym', 'Elevator', 'Security'],
                size: '1200 sq ft',
                images: [
                    'https://images.unsplash.com/photo-1545324418-cc1a3fa10c00?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300',
                    'https://images.unsplash.com/photo-1567016432779-0945037ae304?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
                    'https://images.unsplash.com/photo-1554995207-c18c696e2e50?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                videoUrl: 'https://www.w3schools.com/html/mov_bbb.mp4', // Example video URL
                views: 340, // Added views
                ownerId: 'dummyOwner2'
            },
            {
                id: 'spacious-3bhk-kharghar',
                propertyType: 'Rental',
                title: 'Spacious 3BHK House with Garden',
                rent: 35000,
                area: 1800,
                city: 'Navi Mumbai',
                locality: 'Kharghar',
                state: 'Maharashtra', // Added state
                completeAddress: 'Villa 7, Green Enclave, Sector 10, Kharghar, Navi Mumbai, Maharashtra 410210', // Full address
                partialAddress: 'Sector 10, Kharghar, Navi Mumbai',
                ownerName: 'Vikas Rao',
                contactPhone: '+917766554433',
                contactEmail: 'vikas.r@example.com',
                description: 'A beautiful 3BHK independent house with a lush garden. Perfect for families, located in a peaceful and green locality.',
                furnishedStatus: 'Semi-Furnished',
                amenities: ['Parking', 'Balcony', 'Garden', 'Power Backup'],
                size: '1800 sq ft',
                images: [
                    'https://images.unsplash.com/photo-1522708323590-d24dbb6b0267?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300',
                    'https://images.unsplash.com/photo-1600585152229-ad806231049b?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
                    'https://images.unsplash.com/photo-1593135898086-a79df8996e19?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 210, // Added views
                ownerId: 'dummyOwner1'
            },
            {
                id: 'modern-2bhk-nerul',
                propertyType: 'Rental',
                title: 'Modern 2BHK in Nerul',
                rent: 30000,
                area: 1100,
                city: 'Navi Mumbai',
                locality: 'Nerul',
                state: 'Maharashtra', // Added state
                completeAddress: 'B-501, Tech Residency, Sector 20, Nerul, Navi Mumbai, Maharashtra 400706', // Full address
                partialAddress: 'Sector 20, Nerul, Navi Mumbai',
                ownerName: 'Anil Kumar',
                contactPhone: '+919988776655',
                contactEmail: 'anil.k@example.com',
                description: 'Bright and airy 2BHK, walking distance to major tech parks. Features a spacious living area and modern kitchen appliances.',
                furnishedStatus: 'Furnished',
                amenities: ['AC', 'WiFi', 'Gym', 'Elevator'],
                size: '1100 sq ft',
                images: [
                    'https://images.unsplash.com/photo-1570129477487-eb5c78b54903?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
                    'https://images.unsplash.com/photo-1558000456-07c927c9b0e2?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 95, // Added views
                ownerId: 'dummyOwner3'
            },
            {
                id: 'charming-1bhk-koparkhairane',
                propertyType: 'Rental',
                title: 'Charming 1BHK near Station',
                rent: 17000,
                area: 550,
                city: 'Navi Mumbai',
                locality: 'Koparkhairane',
                state: 'Maharashtra', // Added state
                completeAddress: 'Flat 12A, Metro Homes, Sector 5, Koparkhairane, Navi Mumbai, Maharashtra 400709', // Full address
                partialAddress: 'Sector 5, Koparkhairane, Navi Mumbai',
                ownerName: 'Deepa Verma',
                contactPhone: '+919876512345',
                contactEmail: 'deepa.v@example.com',
                description: 'Ideal 1BHK for singles or couples, excellent station connectivity. Recently renovated with new fixtures.',
                furnishedStatus: 'Semi-Furnished',
                amenities: ['WiFi', 'Power Backup', 'Security'],
                size: '550 sq ft',
                images: [
                    'https://images.unsplash.com/photo-1494526585095-c4146700ecc4?auto=format&fit=crop&w=400&h=300',
                    'https://images.unsplash.com/photo-1494526585095-c4146700ecc4?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 50, // Added views
                ownerId: 'dummyOwner2'
            },
            {
                id: 'cozy-pg-sanpada',
                propertyType: 'PG',
                title: 'Cozy PG for Students',
                rent: 9000,
                area: 120,
                city: 'Navi Mumbai',
                locality: 'Sanpada',
                state: 'Maharashtra', // Added state
                completeAddress: 'Student\'s Haven, Lane 5, Sector 15, Sanpada, Navi Mumbai, Maharashtra 400705', // Full address
                partialAddress: 'Sector 15, Sanpada, Navi Mumbai',
                ownerName: 'Gaurav Kulkarni',
                contactPhone: '+919632107890',
                contactEmail: 'gaurav.k@example.com',
                description: 'Affordable and friendly PG for male students. Close to colleges and coaching centers. Simple meals provided.',
                furnishedStatus: 'Furnished',
                amenities: ['WiFi', 'Meals'],
                size: 'Triple Sharing',
                images: [
                    'https://images.unsplash.com/photo-1596701831872-9a60e0a786d7?auto=format&fit=crop&q=80&w=400&h=300',
                    'https://images.unsplash.com/photo-1596701831872-9a60e0a786d7?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 88, // Added views
                ownerId: 'dummyOwner3'
            },
             {
                id: 'homely-pg-ghansoli',
                propertyType: 'PG',
                title: 'Homely PG for Girls',
                rent: 12000,
                area: 140,
                city: 'Navi Mumbai',
                locality: 'Ghansoli',
                state: 'Maharashtra', // Added state
                completeAddress: 'Girls Nest PG, Road 10, Sector 23, Ghansoli, Navi Mumbai, Maharashtra 400701', // Full address
                partialAddress: 'Sector 23, Ghansoli, Navi Mumbai',
                ownerName: 'Lakshmi Devi',
                contactPhone: '+919543210987',
                contactEmail: 'lakshmi.d@example.com',
                description: 'Safe and secure PG for female students and professionals. Nutritious food and a peaceful environment. Daily housekeeping.',
                furnishedStatus: 'Furnished',
                amenities: ['AC', 'WiFi', 'Meals', 'Housekeeping', 'Security'],
                size: 'Double Sharing',
                images: [
                    'https://images.unsplash.com/photo-1605372138403-1c0500d5a373?auto=format&fit=crop&q=80&w=400&h=300',
                    'https://images.unsplash.com/photo-1605372138403-1c0500d5a373?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 150, // Added views
                ownerId: 'dummyOwner4'
            },
            {
                id: 'cozy-2bhk-kothrud',
                propertyType: 'Rental',
                title: 'Cozy 2BHK in Kothrud',
                rent: 28000,
                area: 900,
                city: 'Pune',
                locality: 'Kothrud',
                state: 'Maharashtra', // Added state
                completeAddress: 'Flat 302, Green Fields, Kothrud, Pune, Maharashtra 411038', // Full address
                partialAddress: 'Kothrud, Pune',
                ownerName: 'Priya Sharma',
                contactPhone: '+919876543210',
                contactEmail: 'priya.s@example.com',
                description: 'A comfortable 2BHK apartment in the popular Kothrud area of Pune. Close to market and public transport.',
                furnishedStatus: 'Semi-Furnished',
                amenities: ['WiFi', 'Security', 'Balcony'],
                size: '900 sq ft',
                images: [
                    'https://images.unsplash.com/photo-1560518883-ff42c3d0d19e?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 70,
                ownerId: 'dummyOwner5'
            }
        ];
        window.dummyRoommates = [
            {
                id: 'rahul-sharma-belapur',
                type: 'want', // Updated type for filtering
                ownerName: 'Rahul Sharma',
                // profession: 'Software Engineer', // Removed as per user request
                age: 28,
                rent: 20000, // This is their budget for shared rent
                city: 'Navi Mumbai',
                locality: 'CBD Belapur',
                state: 'Maharashtra', // Added state
                completeAddress: 'Seeking a 2BHK in CBD Belapur, Navi Mumbai, Maharashtra', // Full address
                partialAddress: 'CBD Belapur, Navi Mumbai',
                contactPhone: '+919012345678',
                contactEmail: 'rahul.sharma@example.com',
                description: 'Friendly and organized software engineer looking for a male roommate. Prefer a non-smoker, clean and quiet environment.',
                preferences: ['Non-Smoker', 'Clean', 'Drinker', 'Vegetarian'],
                gender: 'Male', // Added for analytics
                images: [
                    'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=200',
                    'https://images.unsplash.com/photo-1568602471122-7832951cc4c5?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 75, // Added views
                ownerId: 'dummyRoommateOwner1'
            },
            {
                id: 'ankita-reddy-kharghar',
                type: 'need', // Updated type for filtering
                ownerName: 'Ankita Reddy',
                // profession: 'Marketing Manager', // Removed as per user request
                age: 26,
                rent: 18000, // Budget
                city: 'Navi Mumbai',
                locality: 'Kharghar',
                state: 'Maharashtra', // Added state
                completeAddress: 'Seeking female roommate in Kharghar, Navi Mumbai, Maharashtra', // Full address
                partialAddress: 'Kharghar, Navi Mumbai',
                contactPhone: '+918012345678',
                contactEmail: 'ankita.r@example.com',
                description: 'Looking for a female roommate to share a 2BHK apartment. I enjoy cooking and quiet evenings. Prefer someone clean and respectful.',
                preferences: ['Non-Smoker', 'Clean', 'Drinker', 'Non-Vegetarian'],
                gender: 'Female', // Added for analytics
                images: [
                    'https://images.unsplash.com/photo-1520448100-33b00085a6a0?auto=format&fit=crop&q=80&w=1887&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
                    'https://images.unsplash.com/photo-1504703395950-b054238bc35a?auto=format&fit=crop&q=80&w=2070&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 180, // Added views
                ownerId: 'dummyRoommateOwner2'
            },
            {
                id: 'sameer-khan-vashi',
                type: 'want', // Updated type for filtering
                ownerName: 'Sameer Khan',
                // profession: 'Data Analyst', // Removed as per user request
                age: 29,
                rent: 25000, // Budget
                city: 'Navi Mumbai',
                locality: 'Vashi',
                state: 'Maharashtra', // Added state
                completeAddress: 'Looking for flatmate in Vashi, Navi Mumbai, Maharashtra', // Full address
                partialAddress: 'Vashi, Navi Mumbai',
                contactPhone: '+917012345678',
                contactEmail: 'sameer.k@example.com',
                description: 'Professional seeking male roommate for a 3BHK. I travel frequently for work. Prefer someone independent and tidy.',
                preferences: ['Non-Smoker', 'Pet-Friendly', 'Clean'],
                gender: 'Male', // Added for analytics
                images: [
                    'https://images.unsplash.com/photo-1542909168-82c3e7fd0c8b?auto=format&fit=crop&q=80&w=1887&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
                    'https://images.unsplash.com/photo-1566492031773-4f4e44671857?auto=format&fit=crop&q=80&w=1887&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 42, // Added views
                ownerId: 'dummyRoommateOwner1'
            },
            {
                id: 'priya-shukla-pune',
                type: 'need', // Updated type for filtering
                ownerName: 'Priya Shukla',
                // profession: 'Student', // Removed as per user request
                age: 22,
                rent: 12000,
                city: 'Pune', // Example for non-Navi Mumbai location
                locality: 'Kothrud',
                state: 'Maharashtra', // Added state
                completeAddress: 'Seeking a female roommate for 1BHK in Kothrud, Pune, Maharashtra', // Full address
                partialAddress: 'Kothrud, Pune',
                contactPhone: '+919988771122',
                contactEmail: 'priya.s@example.com',
                description: 'Looking for a friendly and clean female student to share an apartment. I am organized and enjoy quiet study time.',
                preferences: ['Vegetarian', 'Clean', 'Drinker'],
                gender: 'Female',
                images: [
                    'https://placehold.co/400x200/e2e8f0/64748b?text=Priya',
                    'https://images.unsplash.com/photo-1520448100-33b00085a6a0?auto=format&fit=crop&q=80&w=1887&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
                ],
                views: 60, // Added views
                ownerId: 'dummyRoommateOwner2'
            }
        ];
        window.flatmatePreference = 'want'; // Default preference: 'want' for "Want to be Flatmate"
        // --- Core Functions ---
        // Function to toggle between different page sections
        window.showPage = function(pageId) {
            const sections = document.querySelectorAll('.page-section');
            sections.forEach(section => {
                section.classList.remove('active');
            });

           window.showPage = function(pageId) {
        // --- Part 1: Handle Page Content Visibility ---
        // Hide all page sections by removing the 'active' class
        document.querySelectorAll('.page-section').forEach(section => {
            section.classList.remove('active');
        });
        // Show the selected page section by adding the 'active' class
        document.getElementById(pageId).classList.add('active');

        // --- Part 2: Handle Navigation Link Active State (for the "bar" indicator) ---
        // Assuming your navigation links have a common class like 'nav-link'
        // and a 'data-target-page' attribute matching the pageId (e.g., data-target-page="pg")
        document.querySelectorAll('.nav-link').forEach(navLink => {
            navLink.classList.remove('active'); // Remove 'active' from all navigation links
        });
        // Find the specific navigation link for the current page and add 'active'
        const activeNavLink = document.querySelector(`.nav-link[data-target-page="${pageId}"]`);
        if (activeNavLink) {
            activeNavLink.classList.add('active');
        }

        // --- Part 3: Re-render Virtual Beds (already present, just confirming its place) ---
        // This ensures virtual beds are rendered when navigating to PG or Roommates pages
        if (pageId === 'pg') {
            renderVirtualBeds('pg-listings');
        } else if (pageId === 'roommates') {
            renderVirtualBeds('roommate-listings');
        }
    };
            document.getElementById(pageId).classList.add('active');
            // Update active state in navigation
            const navLinks = document.querySelectorAll('.nav-link');
            navLinks.forEach(link => {
                if (link.dataset.page === pageId) {
                    link.classList.add('active');
                } else {
                    link.classList.remove('active');
                }
            });
            // Trigger filters for the displayed page
            if (pageId === 'roommates') {
                window.updateBudgetOutput('roommate'); // Initialize slider display
                window.applyRoommateFilters();
                window.applyPGFilters = function() {
        // Simulate filtering logic
        console.log('Applying PG filters...');
        renderVirtualBeds('pg-listings'); // Re-render beds after filter (simulation)
    };

    window.applyPGFilters = function() {
        // Your existing filter logic would be here
        console.log('Applying PG filters...');
        renderVirtualBeds('pg-listings'); // Add this line to update beds after filtering
    };

    // ... (other functions in between) ...

    window.applyRoommateFilters = function() {
        // Your existing filter logic would be here
        console.log('Applying Roommate filters...');
        renderVirtualBeds('roommate-listings'); // Add this line to update beds after filtering
    };
            } else if (pageId === 'rentals') {
                window.updateBudgetOutput('rental'); // Initialize slider display
                window.applyRentalFilters(); 
            } else if (pageId === 'pg') {
                window.updateBudgetOutput('pg'); // Initialize slider display
                window.applyPGFilters();
            } else if (pageId === 'home') {
                window.displayHomeListings();
            } else if (pageId === 'your-properties') {
                window.displayYourProperties();
            }
        }
        // Toggle mobile menu
        window.toggleMobileMenu = function() {
            const mobileMenu = document.getElementById('mobileMenu');
            const menuIcon = document.getElementById('menuIcon');
            mobileMenu.classList.toggle('hidden');
            if (mobileMenu.classList.contains('hidden')) {
                menuIcon.classList.remove('fa-times');
                menuIcon.classList.add('fa-bars');
            } else {
                menuIcon.classList.remove('fa-bars');
                menuIcon.classList.add('fa-times');
            }
        };
        // --- Modals Functions (Simplified for brevity, assuming existing HTML structure) ---
        window.openSignInModal = function() { document.getElementById('signInModal').classList.add('show'); };
        window.closeSignInModal = function() { document.getElementById('signInModal').classList.remove('show'); };
        window.openForgotPasswordModal = function() {
            document.getElementById('signInModal').classList.remove('show');
            document.getElementById('forgotPasswordModal').classList.add('show');
        };
        window.closeForgotPasswordModal = function() { document.getElementById('forgotPasswordModal').classList.remove('show'); };
        window.backToSignIn = function() {
            document.getElementById('forgotPasswordModal').classList.remove('show');
            document.getElementById('signInModal').classList.add('show');
        };
        window.openPropertyDetailsModal = async function(item) {
            const modal = document.getElementById('propertyDetailsModal');
            const content = document.getElementById('propertyDetailsContent');
            const title = document.getElementById('propertyDetailsTitle');
            title.textContent = item.title;
            // Generate amenities HTML with icons
            let amenitiesHtml = (item.amenities || []).map(a => 
                `<span class="inline-block bg-blue-100 text-blue-800 text-xs px-3 py-1 rounded-full">
                    ${window.amenityEmojis[a] || ''} ${a}
                </span>`
            ).join('');
            
            // Increment view count if Firebase is initialized and item has an ID and is not a dummy item
            if (window.db && item.id && !item.id.startsWith('new-')) { // Avoid incrementing for newly added dummy items
                let collectionPath;
                if (item.propertyType === 'Rental') {
                    collectionPath = `artifacts/${appId}/public/data/rentals`;
                } else if (item.propertyType === 'PG') {
                    collectionPath = `artifacts/${appId}/public/data/pglistings`;
                }
                if (collectionPath) {
                    const docRef = doc(window.db, collectionPath, item.id);
                    try {
                        await updateDoc(docRef, {
                            views: increment(1)
                        });
                        console.log(`View count for ${item.id} incremented.`);
                        // Update the local data for immediate reflection
                        if (item.propertyType === 'Rental') {
                            const index = window.allProperties.findIndex(p => p.id === item.id);
                            if (index !== -1) window.allProperties[index].views = (window.allProperties[index].views || 0) + 1;
                        } else if (item.propertyType === 'PG') {
                            const index = window.allPgListings.findIndex(p => p.id === item.id);
                            if (index !== -1) window.allPgListings[index].views = (window.allPgListings[index].views || 0) + 1;
                        }
                    } catch (error) {
                        console.error("Error incrementing view count: ", error);
                    }
                }
            }
            // Generate media gallery HTML
            let mediaHtml = ``;
            if (item.images && item.images.length > 0) {
                mediaHtml += `<div class="media-gallery relative">`;
                item.images.forEach((img, index) => {
                    mediaHtml += `<img src="${img}" alt="${item.title} Image ${index + 1}" class="${index === 0 ? 'active' : ''} rounded-md shadow-md">`;
                });
                if (item.videoUrl) {
                    mediaHtml += `<video controls class="${item.images.length === 0 ? 'active' : ''} rounded-md shadow-md">
                                    <source src="${item.videoUrl}" type="video/mp4">
                                    Your browser does not support the video tag.
                                </video>`;
                }
                if (item.images.length + (item.videoUrl ? 1 : 0) > 1) {
                    mediaHtml += `<button class="nav-arrow left" onclick="event.stopPropagation(); window.navigateMedia(-1, '${item.id}', 'property')">&#10094;</button>`;
                    mediaHtml += `<button class="nav-arrow right" onclick="event.stopPropagation(); window.navigateMedia(1, '${item.id}', 'property')">&#10095;</button>`;
                }
                mediaHtml += `</div>`;
            } else if (item.videoUrl) {
                 mediaHtml += `<div class="media-gallery relative">
                                <video controls class="active rounded-md shadow-md">
                                    <source src="${item.videoUrl}" type="video/mp4">
                                    Your browser does not support the video tag.
                                </video>`;
            } else {
                mediaHtml += `<div class="media-gallery relative">
                                <img src="https://placehold.co/600x350/e2e8f0/64748b?text=No+Media" alt="No media available" class="active rounded-md shadow-md">
                            </div>`;
            }
            // Check if current user has unlocks available or unlimited access
            const hasUnlocks = window.availableUnlocks > 0 || window.isUnlimitedUnlocks;
            let contactInfoSection;
            if (hasUnlocks) {
                contactInfoSection = `
                    <p class="text-gray-700 font-medium">Address: ${item.completeAddress}</p>
                    <p class="text-gray-700 font-medium">Owner: ${item.ownerName}</p>
                    <p class="text-gray-700 font-medium">Phone: ${item.contactPhone}</p>
                    <p class="text-gray-700 font-medium">Email: ${item.contactEmail || 'N/A'}</p>
                `;
                // Decrement unlock count ONLY if not unlimited access
                if (!window.isUnlimitedUnlocks) {
                    window.availableUnlocks--;
                    localStorage.setItem('bluechipUnlocks', window.availableUnlocks);
                    window.showMessageBox('Unlock Used', `You have ${window.availableUnlocks} unlocks remaining.`, 'info');
                } else {
                    window.showMessageBox('Unlimited Access', 'You have unlimited access to details!', 'success');
                }
            } else {
                contactInfoSection = `
                    <div class="blurred-contact-info">
                        <p class="text-gray-700 font-medium">Address: XXXXXXXXXXXXXXXXXXXX</p>
                        <p class="text-gray-700 font-medium">Owner: XXXXX XXXXX</p>
                        <p class="text-gray-700 font-medium">Phone: XXXXXXXXXX</p>
                        <p class="text-gray-700 font-medium">Email: XXXXXXX@XXXXX.com</p>
                    </div>
                    <div class="unlock-overlay">
                        <button onclick="window.openPaymentModal('${item.id}', 'property')" class="btn-primary text-sm px-4 py-2">
                            <i class="fas fa-lock mr-2"></i>Unlock Details
                        </button>
                    </div>
                `;
            }
            content.innerHTML = `
                ${mediaHtml}
                <p class="text-xl font-semibold text-gray-800 mb-3">₹${item.rent.toLocaleString()}/month</p>
                <div class="details-grid">
                    <div class="detail-item">
                        <p class="detail-label">Location</p>
                        <p class="detail-value">${item.locality}, ${item.city}, ${item.state || 'N/A'}</p>
                    </div>
                    <div class="detail-item">
                        <p class="detail-label">Area</p>
                        <p class="detail-value">${item.area ? item.area + ' sq ft' : 'N/A'}</p>
                    </div>
                    <div class="detail-item">
                        <p class="detail-label">Property Type</p>
                        <p class="detail-value">${item.propertyType === 'Rental' ? item.size : item.propertyType}</p>
                    </div>
                    <div class="detail-item">
                        <p class="detail-label">Furnished Status</p>
                        <p class="detail-value">${item.furnishedStatus}</p>
                    </div>
                    <div class="detail-item">
                        <p class="detail-label">Views</p>
                        <p class="detail-value">${item.views || 0}</p>
                    </div>
                </div>
                <h3 class="text-lg font-semibold text-gray-800 mt-4 mb-2">Description</h3>
                <p class="text-gray-700 leading-relaxed mb-4">${item.description}</p>
                ${amenitiesHtml ? `<h3 class="text-lg font-semibold text-gray-800 mt-4 mb-2">Amenities</h3><div class="flex flex-wrap gap-2 mb-4">${amenitiesHtml}</div>` : ''}
                <h3 class="text-lg font-semibold text-gray-800 mt-4 mb-2">Full Address & Contact</h3>
                <div class="bg-gray-100 p-4 rounded-lg relative">
                    ${contactInfoSection}
                </div>
                <div class="mt-6 flex flex-col sm:flex-row gap-4">
                    <button onclick="window.openInquiryModal('${item.title}')" class="btn-primary flex-1">
                        <i class="fas fa-question-circle mr-2"></i>Inquire Now
                    </button>
                    <button class="bg-darkblue-500 hover:bg-darkblue-600 text-white font-semibold py-2 px-4 rounded-xl shadow-md">
  Check  Availability
</button>

                    
                </div>
            `;
            modal.classList.add('show');
            window.currentViewedItemId = item.id; // Store for media navigation
            window.currentViewedItemType = item.propertyType === 'Rental' ? 'property' : 'pg'; // Store for media navigation
        };
        window.closePropertyDetailsModal = function() { 
            document.getElementById('propertyDetailsModal').classList.remove('show'); 
            window.currentViewedItemId = null;
            window.currentViewedItemType = null;
        };
        window.openRoommateDetailsModal = async function(roommate) {
            const modal = document.getElementById('roommateDetailsModal');
            const content = document.getElementById('roommateDetailsContent');
            const title = document.getElementById('roommateDetailsTitle');
            title.textContent = roommate.ownerName + ' - Roommate Profile';
            // Generate preferences HTML with icons
            let preferencesHtml = (roommate.preferences || []).map(p => 
                `<span class="inline-block bg-purple-100 text-purple-800 text-xs px-3 py-1 rounded-full">
                    ${window.lifestyleEmojis[p] || ''} ${p}
                </span>`
            ).join('');
            
            // Increment view count for roommate profile
            if (window.db && roommate.id && !roommate.id.startsWith('new-')) {
                const docRef = doc(window.db, `artifacts/${appId}/public/data/roommates`, roommate.id);
                try {
                    await updateDoc(docRef, {
                        views: increment(1)
                    });
                    console.log(`View count for roommate ${roommate.id} incremented.`);
                     // Update the local data for immediate reflection
                    const index = window.allRoommates.findIndex(r => r.id === roommate.id);
                    if (index !== -1) window.allRoommates[index].views = (window.allRoommates[index].views || 0) + 1;
                } catch (error) {
                    console.error("Error incrementing roommate view count: ", error);
                }
            }
            let mediaHtml = ``;
            if (roommate.images && roommate.images.length > 0) {
                mediaHtml += `<div class="media-gallery relative">`;
                roommate.images.forEach((img, index) => {
                    mediaHtml += `<img src="${img}" alt="${roommate.ownerName} Image ${index + 1}" class="${index === 0 ? 'active' : ''} rounded-md shadow-md">`;
                });
                // No video for roommates in current dummy data, but including structure
                if (roommate.videoUrl) {
                    mediaHtml += `<video controls class="${roommate.images.length === 0 ? 'active' : ''} rounded-md shadow-md">
                                    <source src="${roommate.videoUrl}" type="video/mp4">
                                    Your browser does not support the video tag.
                                </video>`;
                }
                if (roommate.images.length + (roommate.videoUrl ? 1 : 0) > 1) {
                    mediaHtml += `<button class="nav-arrow left" onclick="event.stopPropagation(); window.navigateMedia(-1, '${roommate.id}', 'roommate')">&#10094;</button>`;
                    mediaHtml += `<button class="nav-arrow right" onclick="event.stopPropagation(); window.navigateMedia(1, '${roommate.id}', 'roommate')">&#10095;</button>`;
                }
                mediaHtml += `</div>`;
            } else {
                mediaHtml += `<div class="media-gallery relative">
                                <img src="https://placehold.co/600x350/e2e8f0/64748b?text=No+Media" alt="No media available" class="active rounded-md shadow-md">
                            </div>`;
            }
            // Check if current user has unlocks available or unlimited access
            const hasUnlocks = window.availableUnlocks > 0 || window.isUnlimitedUnlocks;
            let contactInfoSection;
            if (hasUnlocks) {
                contactInfoSection = `
                    <p class="text-gray-700 font-medium">Name: ${roommate.ownerName}</p>
                    <p class="text-gray-700 font-medium">Phone: ${roommate.contactPhone}</p>
                    <p class="text-gray-700 font-medium">Email: ${roommate.contactEmail || 'N/A'}</p>
                `;
                // Decrement unlock count ONLY if not unlimited access
                if (!window.isUnlimitedUnlocks) {
                    window.availableUnlocks--;
                    localStorage.setItem('bluechipUnlocks', window.availableUnlocks);
                    window.showMessageBox('Unlock Used', `You have ${window.availableUnlocks} unlocks remaining.`, 'info');
                } else {
                    window.showMessageBox('Unlimited Access', 'You have unlimited access to details!', 'success');
                }
            } else {
                contactInfoSection = `
                    <div class="blurred-contact-info">
                        <p class="text-gray-700 font-medium">Name: XXXXX XXXXX</p>
                        <p class="text-gray-700 font-medium">Phone: XXXXXXXXXX</p>
                        <p class="text-gray-700 font-medium">Email: XXXXXXX@XXXXX.com</p>
                    </div>
                    <div class="unlock-overlay">
                        <button onclick="window.openPaymentModal('${roommate.id}', 'roommate')" class="btn-primary text-sm px-4 py-2">
                            <i class="fas fa-lock mr-2"></i>Unlock Details
                        </button>
                    </div>
                `;
            }
            content.innerHTML = `
                ${mediaHtml}
                <p class="text-xl font-semibold text-gray-800 mb-3">Budget: ₹${roommate.rent.toLocaleString()}</p>
                <div class="details-grid">
                    <div class="detail-item">
                        <p class="detail-label">Location</p>
                        <p class="detail-value">${roommate.locality}, ${roommate.city}, ${roommate.state || 'N/A'}</p>
                    </div>
                    <div class="detail-item">
                        <p class="detail-label">Age</p>
                        <p class="detail-value">${roommate.age}</p>
                    </div>
                    <div class="detail-item">
                        <p class="detail-label">Gender</p>
                        <p class="detail-value">${roommate.gender}</p>
                    </div>
                    <div class="detail-item">
                        <p class="detail-label">Views</p>
                        <p class="detail-value">${roommate.views || 0}</p>
                    </div>
                </div>
                <h3 class="text-lg font-semibold text-gray-800 mt-4 mb-2">About Me</h3>
                <p class="text-gray-700 leading-relaxed mb-4">${roommate.description}</p>
                ${preferencesHtml ? `<h3 class="text-lg font-semibold text-gray-800 mt-4 mb-2">Lifestyle Preferences</h3><div class="flex flex-wrap gap-2 mb-4">${preferencesHtml}</div>` : ''}
                <h3 class="text-lg font-semibold text-gray-800 mt-4 mb-2">Contact Details</h3>
                <div class="bg-gray-100 p-4 rounded-lg relative">
                    ${contactInfoSection}
                </div>
                <div class="mt-6 flex flex-col sm:flex-row gap-4">
                    <button onclick="window.openInquiryModal('${roommate.ownerName}\'s Roommate Profile')" class="btn-primary flex-1">
                        <i class="fas fa-question-circle mr-2"></i>Inquire Now
                    </button>
                    <button class="bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-4 rounded-xl shadow-md">
  Check Availability
</button>

                    
                </div>
            `;
            modal.classList.add('show');
            window.currentViewedItemId = roommate.id; // Store for media navigation
            window.currentViewedItemType = 'roommate'; // Store for media navigation
        };
        window.closeRoommateDetailsModal = function() { 
            document.getElementById('roommateDetailsModal').classList.remove('show'); 
            window.currentViewedItemId = null;
            window.currentViewedItemType = null;
        };
        window.openPaymentModal = function(itemId = null, itemType = null) {
            document.getElementById('paymentModal').classList.add('show');
            window.currentViewedItemId = itemId; // Keep track of which item triggered the payment modal
            window.currentViewedItemType = itemType;
        };
        window.closePaymentModal = function() { document.getElementById('paymentModal').classList.remove('show'); };
        window.openListingPaymentModal = function(event) {
            event.preventDefault(); // Prevent default form submission
            // Collect form data before opening modal
            window.tempListingData = {
                propertyTitle: document.getElementById('property-title').value,
                propertyType: document.getElementById('property-type').value,
                monthlyRent: parseInt(document.getElementById('monthly-rent').value),
                areaSqft: parseInt(document.getElementById('area-sqft').value) || null,
                city: document.getElementById('city').value,
                locality: document.getElementById('locality').value,
                // For 'state' in list property, let's assume Navi Mumbai means Maharashtra and Pune means Maharashtra for simplicity
                state: document.getElementById('city').value === 'Navi Mumbai' ? 'Maharashtra' : (document.getElementById('city').value === 'Pune' ? 'Maharashtra' : null), 
                completeAddress: document.getElementById('complete-address').value,
                furnishedStatus: document.querySelector('#furnished-status-options .radio-item.selected')?.dataset.value || 'Unfurnished',
                amenities: Array.from(document.querySelectorAll('#amenity-options .checkbox-item.selected')).map(el => el.dataset.value),
                ownerName: document.getElementById('owner-name').value,
                phoneNumber: document.getElementById('phone-number').value,
                emailAddress: document.getElementById('email-address').value,
                description: document.getElementById('description').value,
                // New optional number fields
                optionalNumber1: parseInt(document.getElementById('phone-number-optional').value) || null, // Corrected ID
                // optionalNumber2: parseInt(document.getElementById('optional-number-2').value) || null, // This ID doesn't exist in HTML
                // Roommate specific fields, only if property type is 'Roommate'
                age: document.getElementById('property-type').value === 'Roommate' ? parseInt(document.getElementById('roommate-age').value) || null : null,
                gender: document.getElementById('property-type').value === 'Roommate' ? document.getElementById('roommate-gender').value : null,
                lifestylePreferences: document.getElementById('property-type').value === 'Roommate' ? Array.from(document.querySelectorAll('#roommate-preferences-options .checkbox-item.selected')).map(el => el.dataset.value) : [],
                ownerId: window.currentUserId, // Assign current user's ID to the listing
                views: 0 // Initialize views to 0
            };
            document.getElementById('listPropertyPaymentModal').classList.add('show');
        };
        window.closeListPropertyPaymentModal = function() { document.getElementById('listPropertyPaymentModal').classList.remove('show'); };
        
        window.openInquiryModal = function(itemTitle = '') {
            document.getElementById('inquiry-property-title').value = itemTitle;
            document.getElementById('inquiryModal').classList.add('show');
        };
        window.closeInquiryModal = function() { document.getElementById('inquiryModal').classList.remove('show'); };
        // Message Box functions
        window.showMessageBox = function(title, message, type = 'info') {
            const msgBox = document.getElementById('messageBox');
            document.getElementById('messageBoxTitle').textContent = title;
            document.getElementById('messageBoxContent').textContent = message;
            const iconDiv = document.getElementById('messageBoxIcon');
            iconDiv.className = 'w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 mt-6'; // Reset classes
            if (type === 'success') {
                iconDiv.innerHTML = '<i class="fas fa-check-circle text-2xl text-green-600"></i>';
                iconDiv.classList.add('bg-green-100');
            } else if (type === 'error') {
                iconDiv.innerHTML = '<i class="fas fa-times-circle text-2xl text-red-600"></i>';
                iconDiv.classList.add('bg-red-100');
            } else { // info or default
                iconDiv.innerHTML = '<i class="fas fa-info-circle text-2xl text-blue-600"></i>';
                iconDiv.classList.add('bg-blue-100');
            }
            msgBox.classList.add('show');
        };
        window.closeMessageBox = function() {
            document.getElementById('messageBox').classList.remove('show');
        };
        // Confirmation Dialog functions
        let confirmCallback = null; // Keeping this local as it's an internal modal state
        window.openConfirmationModal = function(title, message, callback) {
            document.getElementById('confirmationTitle').textContent = title;
            document.getElementById('confirmationMessage').textContent = message;
            confirmCallback = callback;
            document.getElementById('confirmationModal').classList.add('show');
        };
        window.confirmAction = function() {
            if (confirmCallback) {
                confirmCallback(true);
            }
            document.getElementById('confirmationModal').classList.remove('show');
            confirmCallback = null;
        };
        window.cancelConfirmation = function() {
            if (confirmCallback) {
                confirmCallback(false);
            }
            document.getElementById('confirmationModal').classList.remove('show');
            confirmCallback = null;
        };
        // --- Payment & Listing Functions (Simulated) ---
        window.processPaymentForDetailsUnlock = function(planType) {
            window.closePaymentModal();
            let unlocksAdded = 0;
            if (planType === 'single') {
                unlocksAdded = 1;
                window.isUnlimitedUnlocks = false;
            } else if (planType === 'bundle') {
                unlocksAdded = 5;
                window.isUnlimitedUnlocks = false;
            } else if (planType === 'bundle-large') { // NEW
                unlocksAdded = 10;
                window.isUnlimitedUnlocks = false;
            } else if (planType === 'unlimited') { // NEW
                unlocksAdded = 0; // Not adding a count, setting a flag
                window.isUnlimitedUnlocks = true;
                localStorage.setItem('bluechipUnlimitedUnlocks', 'true');
            }

            if (!window.isUnlimitedUnlocks) {
                window.availableUnlocks += unlocksAdded;
                localStorage.setItem('bluechipUnlocks', window.availableUnlocks);
                window.showMessageBox('Payment Successful!', `You have purchased ${unlocksAdded} unlocks. Total unlocks available: ${window.availableUnlocks}.`, 'success');
            } else {
                window.showMessageBox('Payment Successful!', 'You now have UNLIMITED access to contact details!', 'success');
            }
            
            // Re-open the details modal if it was the trigger
            if (window.currentViewedItemId && window.currentViewedItemType) {
                if (window.currentViewedItemType === 'property' || window.currentViewedItemType === 'pg') {
                    const item = window.allProperties.find(p => p.id === window.currentViewedItemId) || window.allPgListings.find(pg => pg.id === window.currentViewedItemId);
                    if (item) window.openPropertyDetailsModal(item);
                } else if (window.currentViewedItemType === 'roommate') {
                    const item = window.allRoommates.find(r => r.id === window.currentViewedItemId);
                    if (item) window.openRoommateDetailsModal(item);
                }
                // Reset current viewed item after showing, to avoid accidental re-unlock
                window.currentViewedItemId = null;
                window.currentViewedItemType = null;
            }
        };
        window.processPaymentForListing = async function() {
            window.closeListPropertyPaymentModal();
            // Here you would send tempListingData to your backend/Firestore
            console.log('Listing Data to be sent:', window.tempListingData);
            if (window.db && window.isAuthReady) {
                try {
                    let collectionName = '';
                    let targetCollection = null;
                    if (window.tempListingData.propertyType === 'Rental') {
                        collectionName = 'rentals';
                        targetCollection = collection(window.db, `artifacts/${appId}/public/data/rentals`);
                    } else if (window.tempListingData.propertyType === 'PG') {
                        collectionName = 'pglistings';
                        targetCollection = collection(window.db, `artifacts/${appId}/public/data/pglistings`);
                    } else if (window.tempListingData.propertyType === 'Roommate') {
                        collectionName = 'roommates';
                        targetCollection = collection(window.db, `artifacts/${appId}/public/data/roommates`);
                    }
                    if (targetCollection) {
                        const newListingData = {
                            status: 'Approved', // Simulate immediate approval for demo
                            images: window.selectedMediaFiles.length > 0 ? window.selectedMediaFiles.map(file => URL.createObjectURL(file)) : ['https://placehold.co/400x200/cccccc/ffffff?text=New+Listing'], // Use selected media or placeholder
                            ...window.tempListingData
                        };
                        const docRef = await addDoc(targetCollection, newListingData);
                        console.log("Document written with ID: ", docRef.id);
                        
                        window.showMessageBox('Success!', 'Your listing has been added and will be visible after review.', 'success');
                        document.getElementById('listPropertyForm').reset(); // Clear form
                        window.selectedMediaFiles = []; // Clear media
                        document.getElementById('media-preview-container').innerHTML = ''; // Clear previews
                        // No need to manually update local arrays; onSnapshot listeners will handle this.
                    } else {
                        window.showMessageBox('Error', 'Invalid property type selected.', 'error');
                    }
                } catch (error) {
                    console.error("Error adding document: ", error);
                    window.showMessageBox('Error', 'Failed to list property. Please try again.', 'error');
                }
            } else {
                 window.showMessageBox('Action Blocked', 'Firebase not initialized or user not authenticated. Cannot save listing.', 'error');
            }
        };
        // --- Contact Functions ---
        window.contactWhatsAppGeneral = function() {
            const message = encodeURIComponent("Hello SetMyStay, I have a general inquiry.");
            window.open(`https://wa.me/${BLUECHIP_CONTACT_NUMBER}?text=${message}`, '_blank');
        };
        window.contactEmailGeneral = function() {
            window.open(`mailto:info@bluechipproperty.com?subject=General Inquiry from Website`, '_blank');
        };
        window.contactWhatsApp = function(phoneNumber) {
            const message = encodeURIComponent("Hello, I am interested in your listing on SetMyStay.");
            window.open(`https://wa.me/${phoneNumber}?text=${message}`, '_blank');
        };
        window.sendInquiryWhatsApp = function() {
            const title = document.getElementById('inquiry-property-title').value;
            const name = document.getElementById('inquiry-user-name').value;
            const phone = document.getElementById('inquiry-user-phone').value;
            const message = document.getElementById('inquiry-message').value;
            if (!name || !phone) {
                window.showMessageBox('Error', 'Please fill in your Name and Phone Number.', 'error');
                return;
            }
            const whatsappMessage = encodeURIComponent(
                `Hello, I am ${name} (${phone}).\n\n` +
                (title ? `I am interested in "${title}".\n\n` : '') +
                (message ? `My message: "${message}"` : `Could you please provide more details?`)
            );
            window.open(`https://wa.me/${BLUECHIP_CONTACT_NUMBER}?text=${whatsappMessage}`, '_blank');
            window.showMessageBox('Inquiry Sent!', 'Your inquiry has been sent via WhatsApp.', 'success');
            window.closeInquiryModal();
        };
        window.sendInquirySMS = function() {
            const title = document.getElementById('inquiry-property-title').value;
            const name = document.getElementById('inquiry-user-name').value;
            const phone = document.getElementById('inquiry-user-phone').value;
            const message = document.getElementById('inquiry-message').value;
            if (!name || !phone) {
                window.showMessageBox('Error', 'Please fill in your Name and Phone Number.', 'error');
                return;
            }
            const smsMessage = encodeURIComponent(
                `Hello, I am ${name} (${phone}). ` +
                (title ? `Interested in "${title}". ` : '') +
                (message ? `Msg: "${message}"` : `Pls share details.`)
            );
            window.open(`sms:${BLUECHIP_CONTACT_NUMBER}?body=${smsMessage}`);
            window.showMessageBox('Inquiry Sent!', 'Your inquiry has been sent via SMS.', 'success');
            window.closeInquiryModal();
        };
        // --- Media Gallery Navigation (for modals) ---
        window.navigateMedia = function(direction, itemId, itemType) {
            let item;
            if (itemType === 'property' || itemType === 'pg') {
                item = window.allProperties.find(p => p.id === itemId) || window.allPgListings.find(pg => pg.id === itemId);
            } else if (itemType === 'roommate') {
                item = window.allRoommates.find(r => r.id === itemId);
            }
            
            if (!item) return;
            const mediaElements = document.querySelectorAll(`#${itemType}DetailsModal .media-gallery img, #${itemType}DetailsModal .media-gallery video`);
            let currentIndex = -1;
            mediaElements.forEach((el, idx) => {
                if (el.classList.contains('active')) {
                    currentIndex = idx;
                }
            });
            mediaElements[currentIndex].classList.remove('active');
            let nextIndex = (currentIndex + direction + mediaElements.length) % mediaElements.length;
            mediaElements[nextIndex].classList.add('active');
        };
        // --- Property Listing Form Toggle Logic ---
        window.togglePropertySpecificFields = function() {
            const propertyType = document.getElementById('property-type').value;
            const furnishedSection = document.getElementById('furnished-status-section');
            const amenitiesSection = document.getElementById('amenities-section');
            const roommateFields = document.getElementById('roommate-specific-fields');
            if (furnishedSection) furnishedSection.style.display = 'none';
            if (amenitiesSection) amenitiesSection.style.display = 'none';
            if (roommateFields) roommateFields.style.display = 'none';
            if (propertyType === 'Rental' || propertyType === 'PG') {
                if (furnishedSection) furnishedSection.style.display = 'block';
                if (amenitiesSection) amenitiesSection.style.display = 'block';
            } else if (propertyType === 'Roommate') {
                if (roommateFields) roommateFields.style.display = 'block';
            }
        };
        // --- Media Upload Handling (List Property Form) ---
        window.handleFileSelect = function(event) {
            const files = event.target.files;
            window.addFilesToPreview(files);
        };
        window.handleDrop = function(event) {
            event.preventDefault();
            const files = event.dataTransfer.files;
            window.addFilesToPreview(files);
        };
        window.addFilesToPreview = function(files) {
            const previewContainer = document.getElementById('media-preview-container');
            let imageCount = window.selectedMediaFiles.filter(file => file.type.startsWith('image')).length;
            let videoCount = window.selectedMediaFiles.filter(file => file.type.startsWith('video')).length;
            for (let i = 0; i < files.length; i++) {
                const file = files[i];
                if (file.type.startsWith('image') && imageCount < MAX_IMAGES) {
                    window.selectedMediaFiles.push(file);
                    imageCount++;
                    window.renderFilePreview(file, previewContainer);
                } else if (file.type.startsWith('video') && videoCount < MAX_VIDEO) {
                    window.selectedMediaFiles.push(file);
                    videoCount++;
                    window.renderFilePreview(file, previewContainer);
                } else {
                    console.warn(`File ${file.name} skipped: Max limit reached or unsupported type.`);
                }
            }
        };
        window.renderFilePreview = function(file, container) {
            const reader = new FileReader();
            reader.onload = function(e) {
                const previewItem = document.createElement('div');
                previewItem.classList.add('preview-item');
                previewItem.dataset.name = file.name;
                if (file.type.startsWith('image')) {
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    previewItem.appendChild(img);
                } else if (file.type.startsWith('video')) {
                    const video = document.createElement('video');
                    video.src = e.target.result;
                    video.controls = false;
                    video.autoplay = false;
                    video.muted = true; // Mute video previews
                    video.playsInline = true;
                    previewItem.appendChild(video);
                }
                const removeBtn = document.createElement('button');
                removeBtn.classList.add('remove-btn');
                removeBtn.innerHTML = '&times;';
                removeBtn.onclick = () => window.removeFilePreview(file.name, previewItem);
                previewItem.appendChild(removeBtn);
                container.appendChild(previewItem);
            };
            reader.readAsDataURL(file);
        };
        window.removeFilePreview = function(fileName, previewElement) {
            window.selectedMediaFiles = window.selectedMediaFiles.filter(file => file.name !== fileName);
            previewElement.remove();
        };
        // --- Filter Toggles for Rentals/PG (from previous snippets) ---
        window.toggleFurnishedFilter = function(element, value) {
            const parent = element.closest('.radio-group');
            Array.from(parent.children).forEach(child => child.classList.remove('selected'));
            element.classList.add('selected');
            window.applyRentalFilters(); // Re-apply filters
        };
        window.toggleAmenityFilter = function(element, value) {
            element.classList.toggle('selected');
            window.applyRentalFilters(); // Re-apply filters
        };
        window.selectFurnishedStatus = function(element, value) {
            const parent = element.closest('.radio-group');
            Array.from(parent.children).forEach(child => child.classList.remove('selected'));
            element.classList.add('selected');
        };
        window.toggleAmenity = function(element, value) {
            element.classList.toggle('selected');
        };
        // Function to select flatmate type ("Want to be Flatmate" or "Need Flatmate")
        window.selectFlatmateType = function(type) {
            window.flatmatePreference = type;
            const wantBtn = document.getElementById('wantFlatmateBtn');
            const needBtn = document.getElementById('needFlatmateBtn');
            if (type === 'want') {
                wantBtn.classList.add('btn-primary');
                wantBtn.classList.remove('btn-secondary');
                needBtn.classList.add('btn-secondary');
                needBtn.classList.remove('btn-primary');
            } else if (type === 'need') {
                needBtn.classList.add('btn-primary');
                needBtn.classList.remove('btn-secondary');
                wantBtn.classList.add('btn-secondary');
                wantBtn.classList.remove('btn-primary');
            }
            window.applyRoommateFilters(); // Re-apply filters with new preference
        };
        // Toggle 'Other' gender input visibility
        window.toggleOtherGenderInput = function() {
            const genderSelect = document.getElementById('roommate-filter-gender');
            const otherGenderInputDiv = document.getElementById('other-gender-input');
            if (genderSelect.value === 'Other') {
                if (otherGenderInputDiv) otherGenderInputDiv.classList.remove('hidden');
            } else {
                if (otherGenderInputDiv) otherGenderInputDiv.classList.add('hidden');
                const genderCustomInput = document.getElementById('genderCustomInput');
                if (genderCustomInput) genderCustomInput.value = ''; // Clear custom input
            }
            window.applyRoommateFilters();
        };
        // Show suggestions for 'Other' gender input
        window.showSuggestions = function(input) {
            const suggestionsList = document.getElementById('suggestionsList');
            if (!suggestionsList) return;
            suggestionsList.innerHTML = '';
            if (input.length < 2) {
                suggestionsList.classList.add('hidden');
                return;
            }
            const filteredSuggestions = window.allGenders.filter(gender =>
                gender.toLowerCase().includes(input.toLowerCase()) && gender.toLowerCase() !== input.toLowerCase()
            );
            if (filteredSuggestions.length > 0) {
                filteredSuggestions.forEach(suggestion => {
                    const listItem = document.createElement('li');
                    listItem.classList.add('px-4', 'py-2', 'cursor-pointer', 'hover:bg-gray-100');
                    listItem.textContent = suggestion;
                    listItem.onclick = () => {
                        const genderCustomInput = document.getElementById('genderCustomInput');
                        if (genderCustomInput) genderCustomInput.value = suggestion;
                        suggestionsList.classList.add('hidden');
                        window.applyRoommateFilters();
                    };
                    suggestionsList.appendChild(listItem);
                });
                suggestionsList.classList.remove('hidden');
            } else {
                suggestionsList.classList.add('hidden');
            }
        };
        
        // Show suggestions for location input
        window.showLocationSuggestions = function(input) {
            const suggestionsList = document.getElementById('locationSuggestionsList');
            if (!suggestionsList) return;
            suggestionsList.innerHTML = '';
            if (input.length < 2) {
                suggestionsList.classList.add('hidden');
                return;
            }
            // Filter and format suggestions
            const uniqueSuggestions = new Set();
            window.locationSuggestionsData.forEach(loc => {
                const fullLocation = `${loc.locality}, ${loc.city}, ${loc.state}`;
                if (fullLocation.toLowerCase().includes(input.toLowerCase())) {
                    uniqueSuggestions.add(fullLocation);
                }
            });
            if (uniqueSuggestions.size > 0) {
                Array.from(uniqueSuggestions).forEach(suggestion => {
                    const listItem = document.createElement('li');
                    listItem.classList.add('px-4', 'py-2', 'cursor-pointer', 'hover:bg-gray-100');
                    listItem.textContent = suggestion;
                    listItem.onclick = () => {
                        const locationInput = document.getElementById('roommate-filter-location-input');
                        if (locationInput) locationInput.value = listItem.textContent;
                        suggestionsList.classList.add('hidden');
                        window.applyRoommateFilters();
                    };
                    suggestionsList.appendChild(listItem);
                });
                suggestionsList.classList.remove('hidden');
            } else {
                suggestionsList.classList.add('hidden');
            }
        };
        // Handle clicks outside suggestions to hide them
        document.addEventListener('click', function(event) {
            const suggestionsList = document.getElementById('suggestionsList');
            const genderCustomInput = document.getElementById('genderCustomInput');
            if (suggestionsList && !suggestionsList.contains(event.target) && genderCustomInput && !genderCustomInput.contains(event.target)) {
                suggestionsList.classList.add('hidden');
            }
            const locationSuggestionsList = document.getElementById('locationSuggestionsList');
            const locationInput = document.getElementById('roommate-filter-location-input');
            if (locationSuggestionsList && !locationSuggestionsList.contains(event.target) && locationInput && !locationInput.contains(event.target)) {
                locationSuggestionsList.classList.add('hidden');
            }
        });

        // Function to update budget output display for sliders
        window.updateBudgetOutput = function(type) {
            let slider, output;
            if (type === 'roommate') {
                slider = document.getElementById('roommate-budget-slider');
                output = document.getElementById('roommate-budget-output');
            } else if (type === 'rental') {
                slider = document.getElementById('rental-budget-slider');
                output = document.getElementById('rental-budget-output');
            } else if (type === 'pg') {
                slider = document.getElementById('pg-budget-slider');
                output = document.getElementById('pg-budget-output');
            }
            if (slider && output) {
                const value = parseInt(slider.value);
                const max = parseInt(slider.max);
                const min = parseInt(slider.min);
                if (value === max) {
                    output.textContent = `Up to ₹${value.toLocaleString()}`;
                } else if (value === min) {
                     output.textContent = `₹${value.toLocaleString()} or more`;
                } else {
                    // For range sliders, let's just show the max budget selected for simplicity,
                    // or convert to a more complex range if a dual-thumb slider is implemented.
                    // For now, we assume the slider value represents the *maximum* budget.
                    output.textContent = `Up to ₹${value.toLocaleString()}`;
                }
                // Also trigger filters
                if (type === 'roommate') {
                    window.applyRoommateFilters();
                } else if (type === 'rental') {
                    window.applyRentalFilters();
                } else if (type === 'pg') {
                    window.applyPGFilters();
                }
            }
        };

        // --- Display Listings Functions ---
        // Function to display roommate listings
        window.displayRoommateListings = function(listings, containerId = 'roommate-listings') {
            const container = document.getElementById(containerId);
            if (!container) return; // Exit if container doesn't exist
            container.innerHTML = ''; // Clear previous listings
            if (listings.length === 0) {
                container.innerHTML = `<p class="text-center text-gray-500 col-span-full">No roommate profiles found matching your criteria.</p>`;
                return;
            }
            listings.forEach(roommate => {
                const card = document.createElement('div');
                card.classList.add('bg-white', 'rounded-xl', 'shadow-lg', 'overflow-hidden', 'property-card');
                // The onclick is directly on the card, which will then open the modal
                card.onclick = () => window.openRoommateDetailsModal(roommate);
                const preferencesHtml = (roommate.preferences || []).slice(0, 3).map(p => 
                    `<span class="inline-block bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">
                        ${window.lifestyleEmojis[p] || ''} ${p}
                    </span>`
                ).join('');
                const additionalPreferencesCount = (roommate.preferences || []).length > 3 ? `+${roommate.preferences.length - 3} more` : '';
                
                card.innerHTML = `
                    <div class="h-48 w-full bg-gray-200 flex items-center justify-center overflow-hidden">
                        <img src="${roommate.images[0] || 'https://placehold.co/400x200/e2e8f0/64748b?text=Roommate'}" alt="${roommate.ownerName}" class="w-full h-full object-cover">
                    </div>
                    <div class="p-5">
                        <h3 class="text-xl font-bold text-gray-900 mb-2">${roommate.ownerName}</h3>
                        <p class="text-blue-600 font-semibold mb-2">Budget: ₹${roommate.rent.toLocaleString()}</p>
                        <p class="text-gray-600 mb-1"><i class="fas fa-map-marker-alt text-gray-400 mr-2"></i>${roommate.locality}, ${roommate.city}</p>
                        <p class="text-gray-600 mb-1"><i class="fas fa-venus-mars text-gray-400 mr-2"></i>${roommate.gender}, ${roommate.age} years old</p>
                        <p class="text-gray-600 mb-3 truncate">${roommate.description}</p>
                        <div class="flex flex-wrap gap-2 text-sm">
                            ${preferencesHtml}
                            ${additionalPreferencesCount ? `<span class="inline-block bg-gray-100 text-gray-700 text-xs px-2 py-1 rounded">${additionalPreferencesCount}</span>` : ''}
                        </div>
                        <div class="text-sm text-gray-500 mt-2">
                            <i class="fas fa-eye mr-1"></i> ${roommate.views || 0} views
                        </div>
                        <button class="mt-4 w-full btn-primary" onclick="event.stopPropagation(); window.openRoommateDetailsModal(window.allRoommates.find(r => r.id === '${roommate.id}'))">
                            View Profile
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
        };
        // Function to display general property listings (Rentals, PG)
        window.displayListings = function(containerId, listings, type) {
            const container = document.getElementById(containerId);
            if (!container) return; // Exit if container doesn't exist
            container.innerHTML = ''; // Clear previous listings
            if (listings.length === 0) {
                container.innerHTML = `<p class="text-center text-gray-500 col-span-full">No ${type} listings found matching your criteria.</p>`;
                return;
            }
            listings.forEach(listing => {
                const card = document.createElement('div');
                card.classList.add('bg-white', 'rounded-xl', 'shadow-lg', 'overflow-hidden', 'property-card');
                card.onclick = () => window.openPropertyDetailsModal(listing); // Use property details modal for both rental and PG
                const amenitiesHtml = (listing.amenities || []).slice(0, 3).map(a => 
                    `<span class="inline-block bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">
                        ${window.amenityEmojis[a] || ''} ${a}
                    </span>`
                ).join('');
                const additionalAmenitiesCount = (listing.amenities || []).length > 3 ? `+${listing.amenities.length - 3} more` : '';
                card.innerHTML = `
                    <div class="h-48 w-full bg-gray-200 flex items-center justify-center overflow-hidden">
                        <img src="${listing.images[0] || 'https://placehold.co/400x200/e2e8f0/64748b?text=Property'}" alt="${listing.title}" class="w-full h-full object-cover">
                    </div>
                    <div class="p-5">
                        <h3 class="text-xl font-bold text-gray-900 mb-2">${listing.title}</h3>
                        <p class="text-blue-600 font-semibold mb-2">₹${listing.rent.toLocaleString()}/month</p>
                        <p class="text-gray-600 mb-1"><i class="fas fa-map-marker-alt text-gray-400 mr-2"></i>${listing.locality}, ${listing.city}</p>
                        <p class="text-gray-600 mb-1"><i class="fas fa-ruler-combined text-gray-400 mr-2"></i>${listing.area} sq ft</p>
                        <p class="text-gray-600 mb-3 truncate">${listing.description}</p>
                        <div class="flex flex-wrap gap-2 text-sm">
                            ${amenitiesHtml}
                            ${additionalAmenitiesCount ? `<span class="inline-block bg-gray-100 text-gray-700 text-xs px-2 py-1 rounded">${additionalAmenitiesCount}</span>` : ''}
                        </div>
                        <div class="text-sm text-gray-500 mt-2">
                            <i class="fas fa-eye mr-1"></i> ${listing.views || 0} views
                        </div>
                        <button class="mt-4 w-full btn-primary" onclick="event.stopPropagation(); window.openPropertyDetailsModal(window.allProperties.find(p => p.id === '${listing.id}') || window.allPgListings.find(pg => pg.id === '${listing.id}'))">
                            View Details
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
        };
        // Function to display featured listings on the home page
        window.displayHomeListings = function() {
            // Shuffle and pick a few properties
            const shuffledProperties = [...window.allProperties, ...window.allPgListings].sort(() => 0.5 - Math.random());
            const propertiesToShow = shuffledProperties.slice(0, 3);
            window.displayListings('home-featured-properties', propertiesToShow, 'property');
            // Shuffle and pick a few roommates
            const shuffledRoommates = [...window.allRoommates].sort(() => 0.5 - Math.random());
            const roommatesToShow = shuffledRoommates.slice(0, 3);
            window.displayRoommateListings(roommatesToShow, 'home-featured-roommates');
        };
        // Function to display user's own listed properties
        window.displayYourProperties = function() {
            const container = document.getElementById('your-listings-container');
            if (!container) return; // Exit if container doesn't exist
            container.innerHTML = ''; // Clear previous content
            // If not authenticated (currentUserId is null or is an anonymous user)
            if (!window.currentUserId || window.isAnonymousUser) {
                container.innerHTML = `
                    <div class="col-span-full text-center py-10 bg-blue-50 rounded-xl shadow-inner border border-blue-200">
                        <i class="fas fa-lock text-blue-500 text-4xl mb-4"></i>
                        <h3 class="text-2xl font-bold text-gray-800 mb-2">Sign In to View Your Properties</h3>
                        <p class="text-gray-600 mb-6">You need to be logged in to access your listed properties. Please sign in or create an account.</p>
                        <button onclick="window.openSignInModal()" class="btn-primary">
                            <i class="fas fa-user mr-2"></i> Sign In
                        </button>
                    </div>
                `;
                return;
            }
            let userListings = [];
            // Filter all properties, PG listings, and roommate profiles by currentUserId
            userListings = userListings.concat(window.allProperties.filter(p => p.ownerId === window.currentUserId));
            userListings = userListings.concat(window.allPgListings.filter(p => p.ownerId === window.currentUserId));
            userListings = userListings.concat(window.allRoommates.filter(r => r.ownerId === window.currentUserId));
            if (userListings.length === 0) {
                container.innerHTML = `
                    <p class="col-span-full text-center text-gray-500 py-8 bg-gray-50 rounded-xl border border-gray-100">
                        You have not listed any properties or roommate profiles yet.
                        <br> <a href="#" onclick="window.showPage('list')" class="text-blue-600 hover:underline mt-2 inline-block">List your first property now!</a>
                    </p>
                `;
            } else {
                userListings.forEach(listing => {
                    const card = document.createElement('div');
                    card.classList.add('bg-white', 'rounded-xl', 'shadow-lg', 'overflow-hidden', 'property-card');
                    card.onclick = () => {
                        if (listing.propertyType === 'Roommate') {
                            window.openRoommateDetailsModal(listing);
                        } else {
                            window.openPropertyDetailsModal(listing);
                        }
                    };
                    // Determine display text based on type
                    const typeText = listing.propertyType === 'Roommate' ? 'Roommate Profile' : listing.propertyType;
                    const titleText = listing.propertyType === 'Roommate' ? listing.ownerName : listing.title;
                    const rentOrBudget = listing.propertyType === 'Roommate' ? `Budget: ₹${listing.rent.toLocaleString()}` : `₹${listing.rent.toLocaleString()}/month`;
                    const locationText = `${listing.locality}, ${listing.city}`;
                    const descriptionText = listing.description;
                    const imageUrl = listing.images && listing.images.length > 0 ? listing.images[0] : 'https://placehold.co/400x200/e2e8f0/64748b?text=Your+Listing';
                    card.innerHTML = `
                        <div class="h-48 w-full bg-gray-200 flex items-center justify-center overflow-hidden">
                            <img src="${imageUrl}" alt="${titleText}" class="w-full h-full object-cover">
                        </div>
                        <div class="p-5">
                            <h3 class="text-xl font-bold text-gray-900 mb-2">${titleText}</h3>
                            <p class="text-blue-600 font-semibold mb-2">${rentOrBudget}</p>
                            <p class="text-gray-600 mb-1"><i class="fas fa-tag text-gray-400 mr-2"></i>${typeText}</p>
                            <p class="text-gray-600 mb-1"><i class="fas fa-map-marker-alt text-gray-400 mr-2"></i>${locationText}</p>
                            <p class="text-gray-600 mb-3 truncate">${descriptionText}</p>
                            <div class="text-lg font-semibold text-gray-800 mt-2">
                                <i class="fas fa-eye text-blue-500 mr-2"></i>Views: ${listing.views || 0}
                            </div>
                            <button class="mt-4 w-full btn-primary" onclick="event.stopPropagation(); 
                                ${listing.propertyType === 'Roommate' ? `window.openRoommateDetailsModal(window.allRoommates.find(r => r.id === '${listing.id}'))` : `window.openPropertyDetailsModal(window.allProperties.find(p => p.id === '${listing.id}') || window.allPgListings.find(pg => pg.id === '${listing.id}'))`}">
                                View Details
                            </button>
                        </div>
                    `;
                    container.appendChild(card);
                });
            }
        };
        // --- Filter Application Functions ---
        window.applyRoommateFilters = function() {
            const locationInput = document.getElementById('roommate-filter-location-input');
            const locationQuery = locationInput ? locationInput.value.toLowerCase() : '';
            const genderSelect = document.getElementById('roommate-filter-gender');
            let gender = genderSelect ? genderSelect.value : '';
            if (gender === 'Other') {
                const genderCustomInput = document.getElementById('genderCustomInput');
                gender = genderCustomInput ? genderCustomInput.value : '';
            }
            
            const budgetSlider = document.getElementById('roommate-budget-slider');
            const maxBudget = budgetSlider ? parseInt(budgetSlider.value) : Infinity;

            let filteredRoommates = window.allRoommates.filter(r => { // Use allRoommates as base (from Firestore or dummy)
                // Ensure gender is accessed safely, `roomate.gender` was a typo, corrected to `r.gender`
                const matchesPreference = (window.flatmatePreference === 'any' || r.type === window.flatmatePreference);
                
                // New logic for detailed location matching
                const fullLocation = `${r.locality}, ${r.city}, ${r.state || ''}`.toLowerCase();
                const matchesLocation = (!locationQuery || fullLocation.includes(locationQuery));
                const matchesGender = (!gender || gender === 'Select Gender' || (r.gender && r.gender.toLowerCase() === gender.toLowerCase()));
                const matchesBudget = (r.rent <= maxBudget); // Only check max budget for slider

                return matchesPreference && matchesLocation && matchesGender && matchesBudget;
            });
            window.displayRoommateListings(filteredRoommates);
        };
        window.applyRentalFilters = function() {
            const furnishedStatusElem = document.querySelector('#rental-furnished-filter .radio-item.selected');
            const furnishedStatus = furnishedStatusElem ? furnishedStatusElem.dataset.value : 'any';
            const selectedAmenitiesElements = document.querySelectorAll('#rental-amenities-filter .checkbox-item.selected');
            const selectedAmenities = Array.from(selectedAmenitiesElements).map(el => el.dataset.value);
            const citySelect = document.getElementById('rental-filter-city');
            const selectedCity = citySelect ? citySelect.value : '';
            
            const localitySelect = document.getElementById('rental-filter-locality');
            const selectedLocality = localitySelect ? localitySelect.value : '';
            const propertyTypeSelect = document.getElementById('rental-filter-type');
            const propertyType = propertyTypeSelect ? propertyTypeSelect.value : '';
            
            const budgetSlider = document.getElementById('rental-budget-slider');
            const maxRent = budgetSlider ? parseInt(budgetSlider.value) : Infinity;
            const minRent = 5000; // Fixed minimum from requirement

            let filteredRentals = window.allProperties.filter(p => p.propertyType === 'Rental');
            if (furnishedStatus !== 'any') {
                filteredRentals = filteredRentals.filter(p => p.furnishedStatus === furnishedStatus);
            }
            if (selectedAmenities.length > 0) {
                filteredRentals = filteredRentals.filter(p => p.amenities && selectedAmenities.every(amenity => p.amenities.includes(amenity)));
            }
            
            if (selectedCity) {
                filteredRentals = filteredRentals.filter(p => p.city === selectedCity);
            }
            if (selectedLocality) {
                filteredRentals = filteredRentals.filter(p => p.locality === selectedLocality);
            }
            if (propertyType) {
                filteredRentals = filteredRentals.filter(p => p.size === propertyType);
            }
            filteredRentals = filteredRentals.filter(p => p.rent >= minRent && p.rent <= maxRent);
            
            window.displayListings('rental-listings', filteredRentals, 'rental');
        };
        window.applyPGFilters = function() {
            const roomTypeSelect = document.getElementById('pg-filter-room-type');
            const roomType = roomTypeSelect ? roomTypeSelect.value : '';
            const citySelect = document.getElementById('pg-filter-city');
            const selectedCity = citySelect ? citySelect.value : '';
            const localitySelect = document.getElementById('pg-filter-locality');
            const selectedLocality = localitySelect ? localitySelect.value : '';
            
            const budgetSlider = document.getElementById('pg-budget-slider');
            const maxRent = budgetSlider ? parseInt(budgetSlider.value) : Infinity;
            const minRent = 2000; // Fixed minimum from requirement
           
            let filteredPgs = window.allPgListings.filter(p => p.propertyType === 'PG');
            if (roomType) {
                filteredPgs = filteredPgs.filter(p => p.size === roomType);
            }
            
            if (selectedCity) {
                filteredPgs = filteredPgs.filter(p => p.city === selectedCity);
            }
            if (selectedLocality) {
                filteredPgs = filteredPgs.filter(p => p.locality === selectedLocality);
            }
            filteredPgs = filteredPgs.filter(p => p.rent >= minRent && p.rent <= maxRent);
            window.displayListings('pg-listings', filteredPgs, 'PG');
        };
        
        // --- Dynamic Filter Population Functions ---
        window.populateCityAndLocalityFilters = function() {
            const rentalCitySelect = document.getElementById('rental-filter-city');
            const pgCitySelect = document.getElementById('pg-filter-city');
            if (!rentalCitySelect || !pgCitySelect) return;
            // Populate City/Region dropdowns
            rentalCitySelect.innerHTML = '<option value="">All Cities</option>';
            pgCitySelect.innerHTML = '<option value="">All Cities</option>';
            // Use unique cities from locationSuggestionsData
            const uniqueCities = [...new Set(window.locationSuggestionsData.map(loc => loc.city))];
            uniqueCities.forEach(city => {
                const option1 = document.createElement('option');
                option1.value = city;
                option1.textContent = city;
                rentalCitySelect.appendChild(option1);
                const option2 = document.createElement('option');
                option2.value = city;
                option2.textContent = city;
                pgCitySelect.appendChild(option2);
            });
            // Set initial selected city if any, then update localities
            // Default to 'Navi Mumbai' if available
            const defaultCity = uniqueCities.includes('Navi Mumbai') ? 'Navi Mumbai' : (uniqueCities[0] || '');
            if (defaultCity) {
                rentalCitySelect.value = defaultCity;
                pgCitySelect.value = defaultCity;
            }
            window.updateLocalityOptions(rentalCitySelect.value, 'rental');
            window.updateLocalityOptions(pgCitySelect.value, 'pg');
        };
        window.updateLocalityOptions = function(selectedCity, type) {
            let localitySelect;
            if (type === 'rental') {
                localitySelect = document.getElementById('rental-filter-locality');
            } else if (type === 'pg') {
                localitySelect = document.getElementById('pg-filter-locality');
            } else {
                return;
            }
            if (!localitySelect) return;
            localitySelect.innerHTML = '<option value="">All Localities</option>'; // Always start with "All Localities"
            if (selectedCity) {
                const localities = new Set();
                window.locationSuggestionsData.forEach(item => {
                    if (item.city === selectedCity && item.locality) {
                        localities.add(item.locality);
                    }
                });
                Array.from(localities).sort().forEach(locality => {
                    const option = document.createElement('option');
                    option.value = locality;
                    option.textContent = locality;
                    localitySelect.appendChild(option);
                });
            }
            // Trigger filter application after updating localities
            if (type === 'rental') {
                window.applyRentalFilters();
            } else if (type === 'pg') {
                window.applyPGFilters();
            }
        };
        // --- Firebase/Data Loading Logic ---
        // Function to fetch data from Firestore
        const fetchData = async () => {
            if (!window.db) {
                console.warn("Firestore not initialized. Using dummy data.");
                window.allProperties = window.dummyProperties.filter(p => p.propertyType === 'Rental');
                window.allPgListings = window.dummyProperties.filter(p => p.propertyType === 'PG');
                window.allRoommates = window.dummyRoommates; 
                
                // Apply filters after dummy data is loaded
                window.populateCityAndLocalityFilters(); // Populate city/locality dropdowns
                window.applyRentalFilters();
                window.applyPGFilters();
                window.applyRoommateFilters();
                window.displayHomeListings();
                window.displayYourProperties(); // Display user properties from dummy data
                return;
            }
            try {
                // Fetch rentals
                const rentalsCol = collection(window.db, `artifacts/${appId}/public/data/rentals`);
                onSnapshot(rentalsCol, (snapshot) => {
                    window.allProperties = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
                    window.populateCityAndLocalityFilters(); // Re-populate city/locality dropdowns after data update
                    window.applyRentalFilters(); // Re-apply filters for rentals
                    window.displayHomeListings(); // Update home section
                    window.displayYourProperties(); // Update your properties section
                }, (error) => {
                    console.error("Error fetching rentals: ", error);
                    window.allProperties = window.dummyProperties.filter(p => p.propertyType === 'Rental');
                    window.populateCityAndLocalityFilters();
                    window.applyRentalFilters();
                    window.displayHomeListings();
                    window.displayYourProperties();
                });
                // Fetch PG listings
                const pgCol = collection(window.db, `artifacts/${appId}/public/data/pglistings`);
                onSnapshot(pgCol, (snapshot) => {
                    window.allPgListings = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
                    window.populateCityAndLocalityFilters(); // Re-populate city/locality dropdowns after data update
                    window.applyPGFilters(); // Re-apply filters for PG
                    window.displayHomeListings(); // Update home section
                    window.displayYourProperties(); // Update your properties section
                }, (error) => {
                    console.error("Error fetching PG listings: ", error);
                    window.allPgListings = window.dummyProperties.filter(p => p.propertyType === 'PG');
                    window.populateCityAndLocalityFilters();
                    window.applyPGFilters();
                    window.displayHomeListings();
                    window.displayYourProperties();
                });
                // Fetch roommate listings
                const roommatesCol = collection(window.db, `artifacts/${appId}/public/data/roommates`);
                onSnapshot(roommatesCol, (snapshot) => {
                    window.allRoommates = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
                    window.applyRoommateFilters(); // Re-apply filters for roommates
                    window.displayHomeListings(); // Update home section
                    window.displayYourProperties(); // Update your properties section
                }, (error) => {
                    console.error("Error fetching roommate listings: ", error);
                    window.allRoommates = window.dummyRoommates;
                    window.applyRoommateFilters();
                    window.displayHomeListings();
                    window.displayYourProperties();
                });
            } catch (e) {
                console.error("Error initializing Firestore listeners: ", e);
                // Fallback to dummy data if Firestore listeners fail
                window.allProperties = window.dummyProperties.filter(p => p.propertyType === 'Rental');
                window.allPgListings = window.dummyProperties.filter(p => p.propertyType === 'PG');
                window.allRoommates = window.dummyRoommates;
                window.populateCityAndLocalityFilters();
                window.applyRentalFilters();
                window.applyPGFilters();
                window.applyRoommateFilters();
                window.displayHomeListings();
                window.displayYourProperties();
            }
        };
        // --- Promo Modal Functions ---
        window.promoModalIntervalId = null;
        const PROMO_INTERVAL_MS = 30000; // 30 seconds
        const INITIAL_PROMO_DELAY_MS = 15000; // 15 seconds
        window.startPromoTimer = function() {
            // Clear any existing timer to prevent duplicates
            if (window.promoModalIntervalId) {
                clearInterval(window.promoModalIntervalId);
            }
            
            // Set an initial delay for the first pop-up
            setTimeout(() => {
                window.tryShowPromoModal();
                // Then set up the repeating interval
                window.promoModalIntervalId = setInterval(window.tryShowPromoModal, PROMO_INTERVAL_MS);
            }, INITIAL_PROMO_DELAY_MS);
        };
        window.tryShowPromoModal = function() {
            // Check if any other modal is currently open
            const openModals = document.querySelectorAll('.modal.show');
            if (openModals.length === 0) {
                // Only show if user has not unlocked any details yet and does not have unlimited access
                if (window.availableUnlocks <= 0 && !window.isUnlimitedUnlocks) {
                    window.openPromoModal();
                }
            }
        };
        window.openPromoModal = function() {
            const promoModal = document.getElementById('promoModal');
            if (promoModal) {
                promoModal.classList.add('show');
            }
        };
        window.closePromoModal = function() {
            const promoModal = document.getElementById('promoModal');
            if (promoModal) {
                promoModal.classList.remove('show');
            }
        };
        // Initialize Firebase and fetch data on DOMContentLoaded
        document.addEventListener('DOMContentLoaded', async () => {
            try {
                if (Object.keys(firebaseConfig).length > 0) {
                    app = initializeApp(firebaseConfig);
                    window.db = getFirestore(app);
                    window.auth = getAuth(app);
                    onAuthStateChanged(window.auth, async (user) => {
                        const yourPropertiesNavLink = document.getElementById('yourPropertiesNavLink');
                        const yourPropertiesNavLinkMobile = document.getElementById('yourPropertiesNavLinkMobile');
                        if (user) {
                            window.currentUserId = user.uid;
                            window.isAnonymousUser = user.isAnonymous; // Set flag
                            console.log("Authenticated with Firebase UID:", window.currentUserId, "Anonymous:", window.isAnonymousUser);
                            
                            // Show 'Your Properties' link if not an anonymous user
                            if (!window.isAnonymousUser) {
                                if (yourPropertiesNavLink) yourPropertiesNavLink.classList.remove('hidden');
                                if (yourPropertiesNavLinkMobile) yourPropertiesNavLinkMobile.classList.remove('hidden');
                            } else {
                                // Hide 'Your Properties' link for anonymous users
                                if (yourPropertiesNavLink) yourPropertiesNavLink.classList.add('hidden');
                                if (yourPropertiesNavLinkMobile) yourPropertiesNavLinkMobile.classList.add('hidden');
                            }
                        } else {
                            // Sign in anonymously if no user is logged in
                            try {
                                const anonUserCredential = await signInAnonymously(window.auth);
                                window.currentUserId = anonUserCredential.user.uid;
                                window.isAnonymousUser = true; // Set flag
                                console.log("Signed in anonymously with UID:", window.currentUserId);
                                // Hide 'Your Properties' link for anonymous users
                                if (yourPropertiesNavLink) yourPropertiesNavLink.classList.add('hidden');
                                if (yourPropertiesNavLinkMobile) yourPropertiesNavLinkMobile.classList.add('hidden');
                            } catch (anonError) {
                                console.error("Error signing in anonymously: ", anonError);
                                // If anonymous sign-in fails, default to no user and hide 'Your Properties'
                                window.currentUserId = null;
                                window.isAnonymousUser = true;
                                if (yourPropertiesNavLink) yourPropertiesNavLink.classList.add('hidden');
                                if (yourPropertiesNavLinkMobile) yourPropertiesNavLinkMobile.classList.add('hidden');
                            }
                        }
                        window.isAuthReady = true;
                        fetchData(); // Fetch data once auth is ready
                        document.getElementById('loadingOverlay').classList.add('hidden'); // Hide loading overlay
                    });
                    document.addEventListener('DOMContentLoaded', () => {
        // ... (Your existing code for populating city/locality, budget, etc. goes here) ...

        // IMPORTANT: Check the currently active page and render beds if it's PG or Roommates
        const activePageId = document.querySelector('.page-section.active')?.id;
        if (activePageId === 'pg') {
            renderVirtualBeds('pg-listings');
        } else if (activePageId === 'roommates') {
            renderVirtualBeds('roommate-listings');
        }
    });
                    // Attempt custom token sign-in if available
                    if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                        try {
                            // onAuthStateChanged above will handle setting currentUserId and isAnonymousUser
                            // based on the result of this sign-in.
                            await signInWithCustomToken(window.auth, __initial_auth_token);
                            console.log("Attempted sign-in with custom token.");
                        } catch (tokenError) {
                            console.error("Error signing in with custom token: ", tokenError);
                        }
                    } else {
                        console.log("No custom auth token provided. Anonymous sign-in will be attempted by onAuthStateChanged.");
                    }
                } else {
                    console.warn("Firebase config not found. Running in demo mode with dummy data.");
                    window.isAuthReady = true; // Still set true to allow dummy data rendering
                    window.isAnonymousUser = true; // Treat as anonymous in demo mode
                    fetchData(); // Use dummy data
                    document.getElementById('loadingOverlay').classList.add('hidden'); // Hide loading overlay
                }
            } catch (e) {
                console.error("Firebase initialization failed: ", e);
                window.isAuthReady = true; // Allow rendering even if Firebase init fails
                window.isAnonymousUser = true;
                fetchData(); // Use dummy data
                document.getElementById('loadingOverlay').classList.add('hidden'); // Hide loading overlay
            }
 
 // Attempt custom token sign-in if available
                    if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                        try {
                            // onAuthStateChanged above will handle setting currentUserId and isAnonymousUser
                            // based on the result of this sign-in.
                            await signInWithCustomToken(window.auth, __initial_auth_token);
                            console.log("Attempted sign-in with custom token.");
                        } catch (tokenError) {
                            console.error("Error signing in with custom token: ", tokenError);
                        }
                    } else {
                        console.log("No custom auth token provided. Anonymous sign-in will be attempted by onAuthStateChanged.");
                    }
           

            // Set default flatmate type and initial filter
            window.selectFlatmateType('want');
            window.togglePropertySpecificFields(); // Initialize display for list property page

            // Add event listeners for city dropdowns to update locality options
            const rentalCitySelect = document.getElementById('rental-filter-city');
            if (rentalCitySelect) {
                rentalCitySelect.addEventListener('change', () => window.updateLocalityOptions(rentalCitySelect.value, 'rental'));
            }
            const pgCitySelect = document.getElementById('pg-filter-city');
            if (pgCitySelect) {
                pgCitySelect.addEventListener('change', () => window.updateLocalityOptions(pgCitySelect.value, 'pg'));
            }
        });

        // Event listeners for budget inputs to trigger filtering
        document.getElementById('roommate-min-budget').addEventListener('input', window.applyRoommateFilters);
        document.getElementById('roommate-max-budget').addEventListener('input', window.applyRoommateFilters);

        // Event listeners for rental filters (re-adding for clarity as they were outside DCL)
        // Note: rental-filter-city and rental-filter-locality changes handled by updateLocalityOptions
        document.getElementById('rental-filter-type').addEventListener('change', window.applyRentalFilters);
        document.getElementById('rental-filter-budget').addEventListener('change', window.applyRentalFilters);
        document.getElementById('rental-filter-locality').addEventListener('change', window.applyRentalFilters); // New listener for locality

        // Event listeners for PG filters (re-adding for clarity as they were outside DCL)
        // Note: pg-filter-city and pg-filter-locality changes handled by updateLocalityOptions
        document.getElementById('pg-filter-room-type').addEventListener('change', window.applyPGFilters);
        document.getElementById('pg-filter-budget').addEventListener('change', window.applyPGFilters);
        document.getElementById('pg-filter-locality').addEventListener('change', window.applyPGFilters); // New listener for locality

        // Handle the login/signup and forgot password forms (placeholders as actual Firebase auth is external)
        window.handleSignIn = function(event) {
            event.preventDefault();
            window.showMessageBox('Sign In Attempt', 'Sign-in functionality is simulated. In a real app, Firebase Authentication would be used.', 'info');
            // Implement actual Firebase authentication here
            // e.g., signInWithEmailAndPassword(auth, email, password);
            window.closeSignInModal();
        };

        window.handleForgotPassword = function(event) {
            event.preventDefault();
            window.showMessageBox('Password Reset', 'Password reset functionality is simulated. In a real app, a password reset email would be sent via Firebase Auth.', 'info');
            // Implement actual Firebase password reset here
            // e.g., sendPasswordResetEmail(auth, email);
            window.closeForgotPasswordModal();
        };
      document.addEventListener('DOMContentLoaded', () => {
        // ... (Your existing code for populating city/locality and budget output, etc. goes here) ...

        // Determine which page section is active on initial load (e.g., 'pg' or 'roommates')
        const initiallyActivePageElement = document.querySelector('.page-section.active');
        if (initiallyActivePageElement) {
            // Get the ID of the active page section
            const initialPageId = initiallyActivePageElement.id;
            // Call showPage for the initial page to correctly set both content and nav bar active states
            window.showPage(initialPageId);
        } else {
            // Fallback: If no page is initially active, default to 'pg' or your desired default
            window.showPage('pg'); // Or whatever your default starting page ID is
        }

        // The renderVirtualBeds calls are now handled inside window.showPage,
        // so you don't need them directly here anymore IF showPage is always called.
        // If you had separate renderVirtualBeds calls here previously, you can remove them.
    });
    
    </script>
    <div id="bedBookingModal" class="modal">
        <div class="modal-content">
            <div class="modal-sticky-header">
                <h3 class="text-2xl font-bold text-gray-900">Book Your Bed</h3>
                <button onclick="window.closeBedBookingModal()" class="text-gray-500 hover:text-gray-700">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            <p class="text-gray-600 mb-6 mt-4">Enter your details to book this bed.</p>
            <form onsubmit="window.submitBedBooking(event)">
                <input type="hidden" id="bedBookingListingId">
                <input type="hidden" id="bedBookingBedNumber">
                <div class="form-group">
                    <label class="form-label">Your Name</label>
                    <input type="text" class="form-input" id="bedBookingName" placeholder="Full Name" required>
                </div>
                <div class="form-group">
                    <label class="form-label">Email Address</label>
                    <input type="email" class="form-input" id="bedBookingEmail" placeholder="your@example.com" required>
                </div>
                <div class="form-group">
                    <label class="form-label">Phone Number</label>
                    <input type="tel" class="form-input" id="bedBookingPhone" placeholder="e.g., +91 9876543210" required>
                </div>
                <div class="form-group">
                    <label class="form-label">Move-in Date</label>
                    <input type="date" class="form-input" id="bedBookingStartDate" required>
                </div>
                <div class="form-group">
                    <label class="form-label">Move-out Date</label>
                    <input type="date" class="form-input" id="bedBookingEndDate" required>
                </div>
                <div class="form-group">
                    <label class="form-label">Bed Description / Requirements</label>
                    <textarea class="form-input" id="bedBookingDescription" rows="3" placeholder="e.g., 'Need a lower bunk bed', 'Drinker roommate preferred'" required></textarea>
                </div>
                <button type="submit" class="btn-primary w-full py-3">
                    <i class="fas fa-check-circle mr-2"></i>
                    Submit Booking Request
                </button>
            </form>
        </div>
    </div>
    
</body>
</html>
