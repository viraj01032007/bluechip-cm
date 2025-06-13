<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BluechipProperty - Premium Property Solutions</title>
    
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
            padding-bottom: 120px;
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
        }

        .nav-link {
            position: relative;
            transition: all 0.3s ease;
            padding: 0.5rem 0;
            text-decoration: none;
            cursor: pointer;
        }
        
        .nav-link:hover {
            color: #2563eb;
        }
        
        .nav-link.active {
            color: #2563eb;
            font-weight: 600;
        }
        
        .nav-link.active::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #2563eb, #3b82f6);
            border-radius: 2px;
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
            padding: 2rem; 
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
            border-color: #2563eb;
            background-color: #2563eb;
            color: white;
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
            border-top: 1px solid #374151;
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

        .blur-address {
            filter: blur(3px);
            user-select: none;
            position: relative;
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
    </style>

</head>

<body class="bg-gray-50">
    <!-- Header -->
    <header class="bg-white shadow-lg sticky top-0 z-40 backdrop-blur-md bg-white/95">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-18">
                <div class="flex items-center space-x-4 cursor-pointer py-2" onclick="showPage('home')">
                    <div class="w-12 h-12 bluechip-gradient rounded-xl flex items-center justify-center shadow-lg">
                        <i class="fas fa-building text-white text-xl"></i>
                    </div>
                    <div>
                        <h1 class="text-2xl font-bold text-gray-900">BluechipProperty</h1>
                        <p class="text-sm text-gray-500 font-medium">Premium Solutions</p>
                    </div>
                </div>
                
                <!-- Mobile Menu Button -->
                <button class="md:hidden p-3 rounded-lg hover:bg-gray-100 transition-colors" onclick="toggleMobileMenu()">
                    <i id="menuIcon" class="fas fa-bars text-gray-700 text-xl"></i>
                </button>
                
                <!-- Desktop Navigation -->
                <nav class="hidden md:flex items-center space-x-8">
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600 active" onclick="showPage('home')" data-page="home">Home</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="showPage('roommates')" data-page="roommates">Roommates</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="showPage('rentals')" data-page="rentals">Rentals</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="showPage('pg')" data-page="pg">PG Listings</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="showPage('list')" data-page="list">List Property</a>
                    
                    <!-- Sign In Button -->
                    <button onclick="openSignInModal()" class="btn-primary ml-4">
                        <i class="fas fa-user mr-2"></i>
                        Sign In
                    </button>
                </nav>
            </div>
            
            <!-- Mobile Navigation -->
            <div id="mobileMenu" class="md:hidden hidden bg-white border-t border-gray-200">
                <div class="px-4 py-4 space-y-3">
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('home'); toggleMobileMenu()">Home</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('roommates'); toggleMobileMenu()">Roommates</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('rentals'); toggleMobileMenu()">Rentals</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('pg'); toggleMobileMenu()">PG Listings</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('list'); toggleMobileMenu()">List Property</a>
                    <button onclick="openSignInModal(); toggleMobileMenu()" class="btn-primary w-full mt-4">
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
                        src="https://images.unsplash.com/photo-1486406146926-c627a92ad1ab?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&h=800" 
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
                                <button onclick="showPage('roommates')" class="btn-primary text-lg px-8 py-4">
                                    <i class="fas fa-users mr-2"></i>
                                    Find Roommates
                                </button>
                                <button onclick="showPage('rentals')" class="btn-secondary text-lg px-8 py-4 bg-white/20 border-white/30 text-white hover:bg-white/30 hover:text-white">
                                    <i class="fas fa-home mr-2"></i>
                                    Browse Rentals
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
                        <h3 class="text-2xl font-bold text-gray-900 mb-4">Find Roommates</h3>
                        <p class="text-gray-600 leading-relaxed">Connect with compatible roommates based on lifestyle preferences, location, and budget requirements.</p>
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
                        <h3 class="text-2xl font-bold text-gray-900 mb-4">PG Accommodations</h3>
                        <p class="text-gray-600 leading-relaxed">Discover comfortable paying guest accommodations with modern amenities and flexible lease terms.</p>
                    </div>
                </div>

                <!-- Sample Properties Section -->
                <div class="mb-12">
                    <h3 class="text-3xl font-bold text-gray-900 mb-8 text-center">Featured Properties</h3>
                    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                        <!-- Sample Property 1 -->
                        <div class="property-card bg-white rounded-xl overflow-hidden shadow-lg">
                            <img 
                                src="https://images.unsplash.com/photo-1545324418-cc1a3fa10c00?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300" 
                                alt="Modern 2BHK Apartment" 
                                class="w-full h-48 object-cover" 
                            />
                            <div class="p-6">
                                <h4 class="text-xl font-bold text-gray-900 mb-2">Luxury 2BHK Apartment</h4>
                                <p class="text-gray-600 mb-4">Sec 15, Bandra West</p>
                                <div class="flex justify-between items-center mb-4">
                                    <span class="text-2xl font-bold text-blue-600">₹45,000/month</span>
                                    <span class="text-sm text-gray-500">1,200 sq ft</span>
                                </div>
                                <div class="flex flex-wrap gap-2 mb-4">
                                    <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">2 BHK</span>
                                    <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Furnished</span>
                                    <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">AC</span>
                                    <span class="bg-orange-100 text-orange-800 text-xs px-2 py-1 rounded">WiFi</span>
                                </div>
                                <button class="btn-primary w-full" onclick="openPropertyDetails('luxury-2bhk')">
                                    <i class="fas fa-eye mr-2"></i>
                                    View Details
                                </button>
                            </div>
                        </div>

                        <!-- Sample Property 2 -->
                        <div class="property-card bg-white rounded-xl overflow-hidden shadow-lg">
                            <img 
                                src="https://images.unsplash.com/photo-1522708323590-d24dbb6b0267?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300" 
                                alt="Spacious 3BHK House" 
                                class="w-full h-48 object-cover" 
                            />
                            <div class="p-6">
                                <h4 class="text-xl font-bold text-gray-900 mb-2">Spacious 3BHK House</h4>
                                <p class="text-gray-600 mb-4">Sec 7, Koramangala</p>
                                <div class="flex justify-between items-center mb-4">
                                    <span class="text-2xl font-bold text-blue-600">₹35,000/month</span>
                                    <span class="text-sm text-gray-500">1,800 sq ft</span>
                                </div>
                                <div class="flex flex-wrap gap-2 mb-4">
                                    <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">3 BHK</span>
                                    <span class="bg-yellow-100 text-yellow-800 text-xs px-2 py-1 rounded">Semi-Furnished</span>
                                    <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">Parking</span>
                                    <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Garden</span>
                                </div>
                                <button class="btn-primary w-full" onclick="openPropertyDetails('spacious-3bhk')">
                                    <i class="fas fa-eye mr-2"></i>
                                    View Details
                                </button>
                            </div>
                        </div>

                        <!-- Sample Property 3 -->
                        <div class="property-card bg-white rounded-xl overflow-hidden shadow-lg">
                            <img 
                                src="https://images.unsplash.com/photo-1586023492125-27b2c045efd7?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300" 
                                alt="Premium PG Accommodation" 
                                class="w-full h-48 object-cover" 
                            />
                            <div class="p-6">
                                <h4 class="text-xl font-bold text-gray-900 mb-2">Premium PG for Professionals</h4>
                                <p class="text-gray-600 mb-4">Sec 14, Gurgaon</p>
                                <div class="flex justify-between items-center mb-4">
                                    <span class="text-2xl font-bold text-blue-600">₹18,000/month</span>
                                    <span class="text-sm text-gray-500">Single Room</span>
                                </div>
                                <div class="flex flex-wrap gap-2 mb-4">
                                    <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">Single</span>
                                    <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Fully Furnished</span>
                                    <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">Meals</span>
                                    <span class="bg-orange-100 text-orange-800 text-xs px-2 py-1 rounded">WiFi</span>
                                </div>
                                <button class="btn-primary w-full" onclick="openPropertyDetails('premium-pg')">
                                    <i class="fas fa-eye mr-2"></i>
                                    View Details
                                </button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Sample Roommates Section -->
                <div class="mb-12">
                    <h3 class="text-3xl font-bold text-gray-900 mb-8 text-center">Featured Roommate Profiles</h3>
                    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                        <!-- Sample Roommate 1 -->
                        <div class="bg-white rounded-xl overflow-hidden shadow-lg hover:shadow-xl transition-all hover:-translate-y-2">
                            <img 
                                src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300" 
                                alt="Roommate profile" 
                                class="w-full h-48 object-cover" 
                            />
                            <div class="p-6">
                                <h4 class="text-xl font-bold text-gray-900 mb-2">Rahul Sharma</h4>
                                <p class="text-gray-600 mb-4">Software Engineer</p>
                                <div class="space-y-2 mb-4">
                                    <div class="flex items-center text-sm text-gray-600">
                                        <i class="fas fa-map-marker-alt mr-2 text-blue-500"></i>
                                        <span>Sec 15, Whitefield</span>
                                    </div>
                                    <div class="flex items-center text-sm text-gray-600">
                                        <i class="fas fa-rupee-sign mr-2 text-green-500"></i>
                                        <span>₹20,000/month budget</span>
                                    </div>
                                </div>
                                <div class="flex flex-wrap gap-2 mb-4">
                                    <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">Non-Smoker</span>
                                    <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Vegetarian</span>
                                    <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">Clean</span>
                                </div>
                                <button class="btn-primary w-full" onclick="openRoommateDetails('rahul-sharma')">
                                    <i class="fas fa-eye mr-2"></i>
                                    View Profile
                                </button>
                            </div>
                        </div>

                        <!-- Additional sample roommates can be added here -->
                    </div>
                </div>
            </div>
        </div>

        <!-- Roommates Page -->
        <div id="roommates" class="page-section">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <h2 class="text-4xl font-bold text-gray-900 mb-8 text-center">Find Your Perfect Roommate</h2>
                <p class="text-xl text-gray-600 text-center mb-12 max-w-3xl mx-auto">
                    Connect with like-minded individuals looking for shared accommodation. Filter by preferences, location, and budget.
                </p>

                <!-- Filters Section -->
                <div class="bg-white rounded-xl shadow-lg p-6 mb-8">
                    <h3 class="text-xl font-bold text-gray-900 mb-4">Filter Roommates</h3>
                    <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
                        <div>
                            <label class="form-label">Location</label>
                            <select class="form-input">
                                <option>All Locations</option>
                                <option>Bangalore</option>
                                <option>Mumbai</option>
                                <option>Delhi NCR</option>
                                <option>Pune</option>
                            </select>
                        </div>
                        <div>
                            <label class="form-label">Budget Range</label>
                            <select class="form-input">
                                <option>Any Budget</option>
                                <option>₹10,000 - ₹15,000</option>
                                <option>₹15,000 - ₹25,000</option>
                                <option>₹25,000 - ₹35,000</option>
                                <option>₹35,000+</option>
                            </select>
                        </div>
                        <div>
                            <label class="form-label">Gender</label>
                            <select class="form-input">
                                <option>Any</option>
                                <option>Male</option>
                                <option>Female</option>
                            </select>
                        </div>
                        <div>
                            <label class="form-label">Profession</label>
                            <select class="form-input">
                                <option>Any Profession</option>
                                <option>Software Engineer</option>
                                <option>Student</option>
                                <option>Doctor</option>
                                <option>Teacher</option>
                            </select>
                        </div>
                    </div>
                </div>

                <!-- Roommate Cards -->
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- Roommate Card 1 -->
                    <div class="bg-white rounded-xl overflow-hidden shadow-lg hover:shadow-xl transition-all hover:-translate-y-2">
                        <img 
                            src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300" 
                            alt="Roommate profile" 
                            class="w-full h-48 object-cover" 
                        />
                        <div class="p-6">
                            <h4 class="text-xl font-bold text-gray-900 mb-2">Rahul Sharma</h4>
                            <p class="text-gray-600 mb-4">Software Engineer</p>
                            <div class="space-y-2 mb-4">
                                <div class="flex items-center text-sm text-gray-600">
                                    <i class="fas fa-map-marker-alt mr-2 text-blue-500"></i>
                                    <span>Sec 15, Whitefield</span>
                                </div>
                                <div class="flex items-center text-sm text-gray-600">
                                    <i class="fas fa-rupee-sign mr-2 text-green-500"></i>
                                    <span>₹20,000/month budget</span>
                                </div>
                            </div>
                            <div class="flex flex-wrap gap-2 mb-4">
                                <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">Non-Smoker</span>
                                <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Vegetarian</span>
                                <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">Clean</span>
                            </div>
                            <button class="btn-primary w-full" onclick="openRoommateDetails('rahul-sharma')">
                                <i class="fas fa-eye mr-2"></i>
                                View Profile
                            </button>
                        </div>
                    </div>

                    <!-- More roommate cards would go here -->
                </div>
            </div>
        </div>

        <!-- Rentals Page -->
        <div id="rentals" class="page-section">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <h2 class="text-4xl font-bold text-gray-900 mb-8 text-center">Premium Rental Properties</h2>
                <p class="text-xl text-gray-600 text-center mb-12 max-w-3xl mx-auto">
                    Discover verified rental properties with complete amenities information and transparent pricing.
                </p>

                <!-- Filters Section -->
                <div class="bg-white rounded-xl shadow-lg p-6 mb-8">
                    <h3 class="text-xl font-bold text-gray-900 mb-4">Filter Properties</h3>
                    
                    <!-- Furnished Status Filter -->
                    <div class="mb-6">
                        <label class="form-label">Furnished Status</label>
                        <div class="radio-group">
                            <div class="radio-item" onclick="toggleFurnishedFilter(this, 'any')">
                                <i class="fas fa-home"></i>
                                <span>Any</span>
                            </div>
                            <div class="radio-item" onclick="toggleFurnishedFilter(this, 'furnished')">
                                <i class="fas fa-couch"></i>
                                <span>Furnished</span>
                            </div>
                            <div class="radio-item" onclick="toggleFurnishedFilter(this, 'semi-furnished')">
                                <i class="fas fa-bed"></i>
                                <span>Semi-Furnished</span>
                            </div>
                            <div class="radio-item" onclick="toggleFurnishedFilter(this, 'unfurnished')">
                                <i class="fas fa-square"></i>
                                <span>Unfurnished</span>
                            </div>
                        </div>
                    </div>

                    <!-- Amenities Filter -->
                    <div class="mb-6">
                        <label class="form-label">Amenities</label>
                        <div class="checkbox-group">
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'ac')">
                                <i class="fas fa-snowflake"></i>
                                <span>Air Conditioning</span>
                            </div>
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'wifi')">
                                <i class="fas fa-wifi"></i>
                                <span>Wi-Fi</span>
                            </div>
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'parking')">
                                <i class="fas fa-car"></i>
                                <span>Parking</span>
                            </div>
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'gym')">
                                <i class="fas fa-dumbbell"></i>
                                <span>Gym</span>
                            </div>
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'pool')">
                                <i class="fas fa-swimming-pool"></i>
                                <span>Swimming Pool</span>
                            </div>
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'elevator')">
                                <i class="fas fa-elevator"></i>
                                <span>Elevator</span>
                            </div>
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'security')">
                                <i class="fas fa-shield-alt"></i>
                                <span>24/7 Security</span>
                            </div>
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'balcony')">
                                <i class="fas fa-door-open"></i>
                                <span>Balcony</span>
                            </div>
                            <div class="checkbox-item" onclick="toggleAmenityFilter(this, 'backup')">
                                <i class="fas fa-bolt"></i>
                                <span>Power Backup</span>
                            </div>
                        </div>
                    </div>

                    <!-- Additional Filters -->
                    <div class="grid md:grid-cols-4 gap-4">
                        <div>
                            <label class="form-label">Location</label>
                            <select class="form-input">
                                <option>All Locations</option>
                                <option>Bandra West</option>
                                <option>Koramangala</option>
                                <option>Whitefield</option>
                                <option>Gurgaon</option>
                            </select>
                        </div>
                        <div>
                            <label class="form-label">Property Type</label>
                            <select class="form-input">
                                <option>All Types</option>
                                <option>1 BHK</option>
                                <option>2 BHK</option>
                                <option>3 BHK</option>
                                <option>4+ BHK</option>
                            </select>
                        </div>
                        <div>
                            <label class="form-label">Budget Range</label>
                            <select class="form-input">
                                <option>Any Budget</option>
                                <option>₹15,000 - ₹25,000</option>
                                <option>₹25,000 - ₹40,000</option>
                                <option>₹40,000 - ₹60,000</option>
                                <option>₹60,000+</option>
                            </select>
                        </div>
                        <div class="flex items-end">
                            <button class="btn-primary w-full">
                                <i class="fas fa-search mr-2"></i>
                                Search
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Property Cards -->
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- Property Card 1 -->
                    <div class="property-card bg-white rounded-xl overflow-hidden shadow-lg">
                        <img 
                            src="https://images.unsplash.com/photo-1545324418-cc1a3fa10c00?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300" 
                            alt="Luxury 2BHK Apartment" 
                            class="w-full h-48 object-cover" 
                        />
                        <div class="p-6">
                            <h4 class="text-xl font-bold text-gray-900 mb-2">Luxury 2BHK Apartment</h4>
                            <p class="text-gray-600 mb-4">Sec 15, Bandra West</p>
                            <div class="flex justify-between items-center mb-4">
                                <span class="text-2xl font-bold text-blue-600">₹45,000/month</span>
                                <span class="text-sm text-gray-500">1,200 sq ft</span>
                            </div>
                            <div class="flex flex-wrap gap-2 mb-4">
                                <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">2 BHK</span>
                                <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Furnished</span>
                                <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">AC</span>
                                <span class="bg-orange-100 text-orange-800 text-xs px-2 py-1 rounded">WiFi</span>
                            </div>
                            <button class="btn-primary w-full" onclick="openPropertyDetails('luxury-2bhk')">
                                <i class="fas fa-eye mr-2"></i>
                                View Details
                            </button>
                        </div>
                    </div>

                    <!-- Property Card 2 -->
                    <div class="property-card bg-white rounded-xl overflow-hidden shadow-lg">
                        <img 
                            src="https://images.unsplash.com/photo-1522708323590-d24dbb6b0267?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300" 
                            alt="Spacious 3BHK House" 
                            class="w-full h-48 object-cover" 
                        />
                        <div class="p-6">
                            <h4 class="text-xl font-bold text-gray-900 mb-2">Spacious 3BHK House</h4>
                            <p class="text-gray-600 mb-4">Sec 7, Koramangala</p>
                            <div class="flex justify-between items-center mb-4">
                                <span class="text-2xl font-bold text-blue-600">₹35,000/month</span>
                                <span class="text-sm text-gray-500">1,800 sq ft</span>
                            </div>
                            <div class="flex flex-wrap gap-2 mb-4">
                                <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">3 BHK</span>
                                <span class="bg-yellow-100 text-yellow-800 text-xs px-2 py-1 rounded">Semi-Furnished</span>
                                <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">Parking</span>
                                <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Garden</span>
                            </div>
                            <button class="btn-primary w-full" onclick="openPropertyDetails('spacious-3bhk')">
                                <i class="fas fa-eye mr-2"></i>
                                View Details
                            </button>
                        </div>
                    </div>

                    <!-- More property cards would go here -->
                </div>
            </div>
        </div>

        <!-- PG Listings Page -->
        <div id="pg" class="page-section">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <h2 class="text-4xl font-bold text-gray-900 mb-8 text-center">PG Accommodations</h2>
                <p class="text-xl text-gray-600 text-center mb-12 max-w-3xl mx-auto">
                    Find comfortable paying guest accommodations with modern amenities and flexible lease terms.
                </p>

                <!-- PG Cards -->
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- PG Card 1 -->
                    <div class="property-card bg-white rounded-xl overflow-hidden shadow-lg">
                        <img 
                            src="https://images.unsplash.com/photo-1586023492125-27b2c045efd7?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=300" 
                            alt="Premium PG" 
                            class="w-full h-48 object-cover" 
                        />
                        <div class="p-6">
                            <h4 class="text-xl font-bold text-gray-900 mb-2">Premium PG for Professionals</h4>
                            <p class="text-gray-600 mb-4">Sec 14, Gurgaon</p>
                            <div class="flex justify-between items-center mb-4">
                                <span class="text-2xl font-bold text-blue-600">₹18,000/month</span>
                                <span class="text-sm text-gray-500">Single Room</span>
                            </div>
                            <div class="flex flex-wrap gap-2 mb-4">
                                <span class="bg-blue-100 text-blue-800 text-xs px-2 py-1 rounded">Single</span>
                                <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded">Meals Included</span>
                                <span class="bg-purple-100 text-purple-800 text-xs px-2 py-1 rounded">AC</span>
                                <span class="bg-orange-100 text-orange-800 text-xs px-2 py-1 rounded">WiFi</span>
                            </div>
                            <button class="btn-primary w-full" onclick="openPropertyDetails('premium-pg')">
                                <i class="fas fa-eye mr-2"></i>
                                View Details
                            </button>
                        </div>
                    </div>

                    <!-- More PG cards would go here -->
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
                    <form id="listPropertyForm" onsubmit="handleListProperty(event)">
                        <!-- Basic Information -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Property Information</h3>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div class="form-group">
                                    <label class="form-label">Property Title</label>
                                    <input type="text" class="form-input" placeholder="e.g., Spacious 2BHK Apartment" required>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Property Type</label>
                                    <select class="form-input" required>
                                        <option value="">Select Type</option>
                                        <option value="1bhk">1 BHK</option>
                                        <option value="2bhk">2 BHK</option>
                                        <option value="3bhk">3 BHK</option>
                                        <option value="4bhk">4+ BHK</option>
                                        <option value="pg">PG</option>
                                        <option value="house">Independent House</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Monthly Rent (₹)</label>
                                    <input type="number" class="form-input" placeholder="25000" required>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Area (sq ft)</label>
                                    <input type="number" class="form-input" placeholder="1200">
                                </div>
                            </div>
                        </div>

                        <!-- Location -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Location</h3>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div class="form-group">
                                    <label class="form-label">City</label>
                                    <select class="form-input" required>
                                        <option value="">Select City</option>
                                        <option value="mumbai">Mumbai</option>
                                        <option value="bangalore">Bangalore</option>
                                        <option value="delhi">Delhi NCR</option>
                                        <option value="pune">Pune</option>
                                        <option value="hyderabad">Hyderabad</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Area/Locality</label>
                                    <input type="text" class="form-input" placeholder="e.g., Bandra West" required>
                                </div>
                                <div class="form-group md:col-span-2">
                                    <label class="form-label">Complete Address</label>
                                    <textarea class="form-input" rows="3" placeholder="Enter complete address with landmarks" required></textarea>
                                </div>
                            </div>
                        </div>

                        <!-- Furnished Status -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Furnished Status</h3>
                            <div class="radio-group">
                                <div class="radio-item" onclick="selectFurnishedStatus(this, 'furnished')">
                                    <i class="fas fa-couch"></i>
                                    <span>Furnished</span>
                                </div>
                                <div class="radio-item" onclick="selectFurnishedStatus(this, 'semi-furnished')">
                                    <i class="fas fa-bed"></i>
                                    <span>Semi-Furnished</span>
                                </div>
                                <div class="radio-item" onclick="selectFurnishedStatus(this, 'unfurnished')">
                                    <i class="fas fa-square"></i>
                                    <span>Unfurnished</span>
                                </div>
                            </div>
                        </div>

                        <!-- Amenities -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Available Amenities</h3>
                            <div class="checkbox-group">
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'ac')">
                                    <i class="fas fa-snowflake"></i>
                                    <span>Air Conditioning</span>
                                </div>
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'wifi')">
                                    <i class="fas fa-wifi"></i>
                                    <span>Wi-Fi</span>
                                </div>
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'parking')">
                                    <i class="fas fa-car"></i>
                                    <span>Parking</span>
                                </div>
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'gym')">
                                    <i class="fas fa-dumbbell"></i>
                                    <span>Gym</span>
                                </div>
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'pool')">
                                    <i class="fas fa-swimming-pool"></i>
                                    <span>Swimming Pool</span>
                                </div>
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'elevator')">
                                    <i class="fas fa-elevator"></i>
                                    <span>Elevator</span>
                                </div>
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'security')">
                                    <i class="fas fa-shield-alt"></i>
                                    <span>24/7 Security</span>
                                </div>
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'balcony')">
                                    <i class="fas fa-door-open"></i>
                                    <span>Balcony</span>
                                </div>
                                <div class="checkbox-item" onclick="toggleAmenity(this, 'backup')">
                                    <i class="fas fa-bolt"></i>
                                    <span>Power Backup</span>
                                </div>
                            </div>
                        </div>

                        <!-- Contact Information -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Contact Information</h3>
                            <div class="grid md:grid-cols-2 gap-6">
                                <div class="form-group">
                                    <label class="form-label">Owner Name</label>
                                    <input type="text" class="form-input" placeholder="Your full name" required>
                                </div>
                                <div class="form-group">
                                    <label class="form-label">Phone Number</label>
                                    <input type="tel" class="form-input" placeholder="+91 98765 43210" required>
                                </div>
                                <div class="form-group md:col-span-2">
                                    <label class="form-label">Email Address (Optional)</label>
                                    <input type="email" class="form-input" placeholder="your.email@example.com">
                                </div>
                            </div>
                        </div>

                        <!-- Additional Details -->
                        <div class="mb-8">
                            <h3 class="text-xl font-bold text-gray-900 mb-4">Additional Details</h3>
                            <div class="form-group">
                                <label class="form-label">Property Description</label>
                                <textarea class="form-input" rows="4" placeholder="Describe your property, nearby landmarks, transportation, etc."></textarea>
                            </div>
                        </div>

                        <button type="submit" class="btn-primary w-full text-lg">
                            <i class="fas fa-plus mr-2"></i>
                            List Property
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </main>

    <!-- Floating Contact Buttons -->
    <div class="floating-contacts">
        <button class="floating-btn whatsapp-btn" onclick="contactWhatsApp()" title="WhatsApp Support">
            <i class="fab fa-whatsapp"></i>
        </button>
        <button class="floating-btn email-btn" onclick="contactEmail()" title="Email Support">
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
                        <h3 class="text-xl font-bold">BluechipProperty</h3>
                        <p class="text-sm text-gray-400">Premium Solutions</p>
                    </div>
                </div>
                <p class="text-gray-300 mb-4">
                    Your trusted partner for finding the perfect living space. Connecting people with their ideal homes since 2024.
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
                    <li><a href="#" onclick="showPage('roommates')">Find Roommates</a></li>
                    <li><a href="#" onclick="showPage('rentals')">Rental Properties</a></li>
                    <li><a href="#" onclick="showPage('pg')">PG Accommodations</a></li>
                    <li><a href="#" onclick="showPage('list')">List Property</a></li>
                    <li><a href="#">Property Management</a></li>
                </ul>
            </div>

            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul>
                    <li><a href="#" onclick="showPage('home')">Home</a></li>
                    <li><a href="#">About Us</a></li>
                    <li><a href="#">How It Works</a></li>
                    <li><a href="#">Pricing</a></li>
                    <li><a href="#">Blog</a></li>
                </ul>
            </div>

            <div class="footer-section">
                <h3>Support</h3>
                <ul>
                    <li><a href="#">Help Center</a></li>
                    <li><a href="#">Contact Us</a></li>
                    <li><a href="#">Privacy Policy</a></li>
                    <li><a href="#">Terms of Service</a></li>
                    <li><a href="#">Safety Guidelines</a></li>
                </ul>
            </div>
        </div>

        <div class="footer-bottom">
            <p>&copy; 2024 BluechipProperty. All rights reserved. | Designed with ❤️ for better living</p>
        </div>
    </footer>

    <!-- Sign In Modal -->
    <div id="signInModal" class="modal">
        <div class="modal-content">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-900">Welcome Back</h2>
                <button onclick="closeSignInModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <!-- Social Login Buttons -->
            <div class="space-y-3 mb-6">
                <button class="btn-social btn-google">
                    <i class="fab fa-google text-red-500"></i>
                    <span>Continue with Google</span>
                </button>
                <button class="btn-social btn-twitter">
                    <i class="fab fa-twitter text-blue-500"></i>
                    <span>Continue with Twitter</span>
                </button>
            </div>

            <div class="divider">
                <span>or sign in with email</span>
            </div>

            <form id="signInForm" onsubmit="handleSignIn(event)">
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
                    <a href="#" onclick="openForgotPasswordModal()" class="forgot-password-link">
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
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-900">Reset Password</h2>
                <button onclick="closeForgotPasswordModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <form id="forgotPasswordForm" onsubmit="handleForgotPassword(event)">
                <div class="form-group">
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
                <button onclick="backToSignIn()" class="text-blue-600 hover:text-blue-700 font-medium">
                    <i class="fas fa-arrow-left mr-2"></i>
                    Back to Sign In
                </button>
            </div>
        </div>
    </div>

    <!-- Property Details Modal -->
    <div id="propertyDetailsModal" class="modal">
        <div class="modal-content" style="max-width: 800px;">
            <div class="flex justify-between items-center mb-6">
                <h2 id="propertyDetailsTitle" class="text-2xl font-bold text-gray-900">Property Details</h2>
                <button onclick="closePropertyDetailsModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <div id="propertyDetailsContent">
                <!-- Content will be dynamically inserted -->
            </div>
        </div>
    </div>

    <!-- Roommate Details Modal -->
    <div id="roommateDetailsModal" class="modal">
        <div class="modal-content" style="max-width: 800px;">
            <div class="flex justify-between items-center mb-6">
                <h2 id="roommateDetailsTitle" class="text-2xl font-bold text-gray-900">Roommate Profile</h2>
                <button onclick="closeRoommateDetailsModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <div id="roommateDetailsContent">
                <!-- Content will be dynamically inserted -->
            </div>
        </div>
    </div>

    <!-- Payment Modal for Address -->
    <div id="paymentModal" class="modal">
        <div class="modal-content" style="max-width: 500px;">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-900">Unlock Full Address</h2>
                <button onclick="closePaymentModal()" class="text-gray-400 hover:text-gray-600">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <div class="text-center mb-6">
                <div class="w-20 h-20 bg-yellow-100 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-lock text-yellow-600 text-2xl"></i>
                </div>
                <h3 class="text-xl font-semibold text-gray-900 mb-2">Premium Feature</h3>
                <p class="text-gray-600">Get access to complete address and contact details</p>
            </div>

            <div class="bg-blue-50 rounded-lg p-4 mb-6">
                <div class="flex justify-between items-center">
                    <div>
                        <h4 class="font-semibold text-gray-900">Address Unlock</h4>
                        <p class="text-sm text-gray-600">One-time payment for full details</p>
                    </div>
                    <div class="text-right">
                        <span class="text-2xl font-bold text-blue-600">₹149</span>
                    </div>
                </div>
            </div>

            <div class="space-y-4 mb-6">
                <div class="flex items-center text-sm text-gray-600">
                    <i class="fas fa-check text-green-500 mr-3"></i>
                    <span>Complete property address</span>
                </div>
                <div class="flex items-center text-sm text-gray-600">
                    <i class="fas fa-check text-green-500 mr-3"></i>
                    <span>Owner contact information</span>
                </div>
                <div class="flex items-center text-sm text-gray-600">
                    <i class="fas fa-check text-green-500 mr-3"></i>
                    <span>Direct WhatsApp contact</span>
                </div>
                <div class="flex items-center text-sm text-gray-600">
                    <i class="fas fa-check text-green-500 mr-3"></i>
                    <span>Property location on map</span>
                </div>
            </div>

            <button onclick="processPayment()" class="btn-primary w-full text-lg">
                <i class="fas fa-credit-card mr-2"></i>
                Pay ₹149 & Unlock Details
            </button>

            <p class="text-xs text-gray-500 text-center mt-4">
                Secure payment powered by BluechipProperty
            </p>
        </div>
    </div>

    <script>
        // Property data with partial addresses
        const propertyData = {
            'luxury-2bhk': {
                name: 'Luxury 2BHK Apartment',
                price: '₹45,000/month',
                size: '1,200 sq ft',
                type: '2 BHK',
                furnished: 'Furnished',
                partialAddress: 'Sec 15, Bandra West',
                fullAddress: 'Building A-302, Sector 15, Bandra West, Mumbai 400050',
                amenities: ['AC', 'WiFi', 'Parking', 'Gym', 'Swimming Pool', 'Security'],
                description: 'Spacious 2BHK apartment with modern amenities and great connectivity.',
                contact: '+91 98765 43210',
                ownerName: 'Raj Patel',
                images: ['https://images.unsplash.com/photo-1545324418-cc1a3fa10c00?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600']
            },
            'spacious-3bhk': {
                name: 'Spacious 3BHK House',
                price: '₹35,000/month',
                size: '1,800 sq ft',
                type: '3 BHK',
                furnished: 'Semi-Furnished',
                partialAddress: 'Sec 7, Koramangala',
                fullAddress: 'House No. 42, 7th Block, Koramangala, Bangalore 560095',
                amenities: ['Parking', 'Garden', 'WiFi', 'Security', 'Power Backup'],
                description: 'Independent house with garden and ample parking space.',
                contact: '+91 98123 45678',
                ownerName: 'Priya Sharma',
                images: ['https://images.unsplash.com/photo-1522708323590-d24dbb6b0267?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600']
            },
            'premium-pg': {
                name: 'Premium PG for Professionals',
                price: '₹18,000/month',
                size: 'Single Room',
                type: 'PG',
                furnished: 'Fully Furnished',
                partialAddress: 'Sec 14, Gurgaon',
                fullAddress: 'Block C-201, Sector 14, Gurgaon, Haryana 122001',
                amenities: ['Meals', 'WiFi', 'AC', 'Laundry', 'Security', 'Housekeeping'],
                description: 'Premium PG accommodation with all meals and modern facilities.',
                contact: '+91 98234 56789',
                ownerName: 'Amit Kumar',
                images: ['https://images.unsplash.com/photo-1586023492125-27b2c045efd7?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600']
            }
        };

        const roommateData = {
            'rahul-sharma': {
                name: 'Rahul Sharma',
                profession: 'Software Engineer',
                age: 26,
                partialAddress: 'Sec 15, Whitefield',
                fullAddress: 'Prestige Tech Park, Sector 15, Whitefield, Bangalore 560066',
                budget: '₹20,000/month',
                preferences: ['Non-Smoker', 'Vegetarian', 'Clean', 'Quiet'],
                contact: '+91 98765 12345',
                email: 'rahul.sharma@email.com',
                description: 'Working professional looking for a clean and peaceful living environment.',
                images: ['https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&h=400']
            }
        };

        let currentPropertyId = null;
        let hasUnlockedAddress = false;

        // Navigation and page switching
        function showPage(pageId) {
            // Hide all pages
            const pages = document.querySelectorAll('.page-section');
            pages.forEach(page => page.classList.remove('active'));

            // Show selected page
            document.getElementById(pageId).classList.add('active');

            // Update nav links
            const navLinks = document.querySelectorAll('.nav-link');
            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('data-page') === pageId) {
                    link.classList.add('active');
                }
            });

            // Close mobile menu if open
            const mobileMenu = document.getElementById('mobileMenu');
            mobileMenu.classList.add('hidden');
            document.getElementById('menuIcon').className = 'fas fa-bars text-gray-700 text-xl';
        }

        // Mobile menu toggle
        function toggleMobileMenu() {
            const mobileMenu = document.getElementById('mobileMenu');
            const menuIcon = document.getElementById('menuIcon');
            
            if (mobileMenu.classList.contains('hidden')) {
                mobileMenu.classList.remove('hidden');
                menuIcon.className = 'fas fa-times text-gray-700 text-xl';
            } else {
                mobileMenu.classList.add('hidden');
                menuIcon.className = 'fas fa-bars text-gray-700 text-xl';
            }
        }

        // Modal functions
        function openSignInModal() {
            document.getElementById('signInModal').classList.add('show');
        }

        function closeSignInModal() {
            document.getElementById('signInModal').classList.remove('show');
        }

        function openForgotPasswordModal() {
            closeSignInModal();
            document.getElementById('forgotPasswordModal').classList.add('show');
        }

        function closeForgotPasswordModal() {
            document.getElementById('forgotPasswordModal').classList.remove('show');
        }

        function backToSignIn() {
            closeForgotPasswordModal();
            openSignInModal();
        }

        // Form handlers
        function handleSignIn(event) {
            event.preventDefault();
            alert('Sign in functionality would be implemented here');
            closeSignInModal();
        }

        function handleForgotPassword(event) {
            event.preventDefault();
            alert('Password reset link sent to your email!');
            closeForgotPasswordModal();
        }

        // Floating contact functions
        function contactWhatsApp() {
            const phoneNumber = '919876543210';
            const message = 'Hi! I need help with BluechipProperty services.';
            const whatsappUrl = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
            window.open(whatsappUrl, '_blank');
        }

        function contactEmail() {
            const email = 'support@bluechipproperty.com';
            const subject = 'Support Request - BluechipProperty';
            const body = 'Hi,\n\nI need assistance with BluechipProperty services.\n\nRegards';
            const emailUrl = `mailto:${email}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
            window.location.href = emailUrl;
        }

        // Property Details Functions
        function openPropertyDetails(propertyId) {
            currentPropertyId = propertyId;
            const property = propertyData[propertyId];
            if (!property) return;

            document.getElementById('propertyDetailsTitle').textContent = property.name;
            
            const content = `
                <div class="space-y-6">
                    <img src="${property.images[0]}" alt="${property.name}" class="w-full h-64 object-cover rounded-lg">
                    
                    <div class="details-grid">
                        <div class="detail-item">
                            <div class="detail-label">Price</div>
                            <div class="detail-value text-2xl font-bold text-blue-600">${property.price}</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Size</div>
                            <div class="detail-value">${property.size}</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Type</div>
                            <div class="detail-value">${property.type}</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Furnished</div>
                            <div class="detail-value">${property.furnished}</div>
                        </div>
                    </div>

                    <div class="bg-gray-50 p-4 rounded-lg">
                        <div class="detail-label mb-2">Address</div>
                        <div class="relative">
                            <div class="${hasUnlockedAddress ? '' : 'blur-address'}">${hasUnlockedAddress ? property.fullAddress : property.partialAddress}</div>
                            ${!hasUnlockedAddress ? `
                                <div class="unlock-overlay">
                                    <button onclick="openPaymentModal()" class="bg-blue-600 text-white px-4 py-2 rounded-lg text-sm font-medium hover:bg-blue-700">
                                        <i class="fas fa-lock mr-2"></i>Unlock Full Address
                                    </button>
                                </div>
                            ` : ''}
                        </div>
                    </div>

                    <div>
                        <div class="detail-label mb-3">Amenities</div>
                        <div class="flex flex-wrap gap-2">
                            ${property.amenities.map(amenity => `
                                <span class="bg-blue-100 text-blue-800 text-sm px-3 py-1 rounded-full">${amenity}</span>
                            `).join('')}
                        </div>
                    </div>

                    <div>
                        <div class="detail-label mb-2">Description</div>
                        <div class="detail-value">${property.description}</div>
                    </div>

                    ${hasUnlockedAddress ? `
                        <div class="bg-green-50 p-4 rounded-lg">
                            <div class="detail-label mb-2">Contact Information</div>
                            <div class="space-y-2">
                                <div class="detail-value">Owner: ${property.ownerName}</div>
                                <div class="detail-value">Phone: ${property.contact}</div>
                            </div>
                        </div>
                        
                        <div class="flex gap-4">
                            <button onclick="contactViaWhatsApp('${property.contact}', '${property.name}')" class="btn-primary flex-1">
                                <i class="fab fa-whatsapp mr-2"></i>WhatsApp
                            </button>
                            <button onclick="contactViaCall('${property.contact}')" class="btn-secondary flex-1">
                                <i class="fas fa-phone mr-2"></i>Call Now
                            </button>
                        </div>
                    ` : `
                        <div class="bg-yellow-50 border border-yellow-200 p-4 rounded-lg">
                            <div class="flex items-center text-yellow-800">
                                <i class="fas fa-info-circle mr-2"></i>
                                <span class="text-sm">Unlock full address and contact details for ₹149</span>
                            </div>
                        </div>
                    `}
                </div>
            `;
            
            document.getElementById('propertyDetailsContent').innerHTML = content;
            document.getElementById('propertyDetailsModal').classList.add('show');
        }

        function openRoommateDetails(roommateId) {
            const roommate = roommateData[roommateId];
            if (!roommate) return;

            document.getElementById('roommateDetailsTitle').textContent = roommate.name;
            
            const content = `
                <div class="space-y-6">
                    <div class="flex items-center space-x-4">
                        <img src="${roommate.images[0]}" alt="${roommate.name}" class="w-24 h-24 object-cover rounded-full">
                        <div>
                            <h3 class="text-xl font-bold">${roommate.name}</h3>
                            <p class="text-gray-600">${roommate.profession}</p>
                            <p class="text-gray-500">Age: ${roommate.age}</p>
                        </div>
                    </div>
                    
                    <div class="details-grid">
                        <div class="detail-item">
                            <div class="detail-label">Budget</div>
                            <div class="detail-value text-lg font-semibold text-blue-600">${roommate.budget}</div>
                        </div>
                        <div class="detail-item">
                            <div class="detail-label">Profession</div>
                            <div class="detail-value">${roommate.profession}</div>
                        </div>
                    </div>

                    <div class="bg-gray-50 p-4 rounded-lg">
                        <div class="detail-label mb-2">Preferred Location</div>
                        <div class="relative">
                            <div class="${hasUnlockedAddress ? '' : 'blur-address'}">${hasUnlockedAddress ? roommate.fullAddress : roommate.partialAddress}</div>
                            ${!hasUnlockedAddress ? `
                                <div class="unlock-overlay">
                                    <button onclick="openPaymentModal()" class="bg-blue-600 text-white px-4 py-2 rounded-lg text-sm font-medium hover:bg-blue-700">
                                        <i class="fas fa-lock mr-2"></i>Unlock Full Details
                                    </button>
                                </div>
                            ` : ''}
                        </div>
                    </div>

                    <div>
                        <div class="detail-label mb-3">Preferences</div>
                        <div class="flex flex-wrap gap-2">
                            ${roommate.preferences.map(pref => `
                                <span class="bg-green-100 text-green-800 text-sm px-3 py-1 rounded-full">${pref}</span>
                            `).join('')}
                        </div>
                    </div>

                    <div>
                        <div class="detail-label mb-2">About</div>
                        <div class="detail-value">${roommate.description}</div>
                    </div>

                    ${hasUnlockedAddress ? `
                        <div class="bg-green-50 p-4 rounded-lg">
                            <div class="detail-label mb-2">Contact Information</div>
                            <div class="space-y-2">
                                <div class="detail-value">Phone: ${roommate.contact}</div>
                                <div class="detail-value">Email: ${roommate.email}</div>
                            </div>
                        </div>
                        
                        <div class="flex gap-4">
                            <button onclick="contactViaWhatsApp('${roommate.contact}', 'roommate connection')" class="btn-primary flex-1">
                                <i class="fab fa-whatsapp mr-2"></i>WhatsApp
                            </button>
                            <button onclick="contactViaEmail('${roommate.email}', '${roommate.name}')" class="btn-secondary flex-1">
                                <i class="fas fa-envelope mr-2"></i>Email
                            </button>
                        </div>
                    ` : `
                        <div class="bg-yellow-50 border border-yellow-200 p-4 rounded-lg">
                            <div class="flex items-center text-yellow-800">
                                <i class="fas fa-info-circle mr-2"></i>
                                <span class="text-sm">Unlock contact details for ₹149</span>
                            </div>
                        </div>
                    `}
                </div>
            `;
            
            document.getElementById('roommateDetailsContent').innerHTML = content;
            document.getElementById('roommateDetailsModal').classList.add('show');
        }

        // Payment and Address Unlocking
        function openPaymentModal() {
            document.getElementById('paymentModal').classList.add('show');
        }

        function closePaymentModal() {
            document.getElementById('paymentModal').classList.remove('show');
        }

        function processPayment() {
            // Simulate payment processing
            const paymentModal = document.getElementById('paymentModal');
            paymentModal.innerHTML = `
                <div class="modal-content" style="max-width: 500px;">
                    <div class="text-center py-8">
                        <div class="w-20 h-20 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class="fas fa-check text-green-600 text-2xl"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-gray-900 mb-2">Payment Successful!</h3>
                        <p class="text-gray-600 mb-6">Address and contact details have been unlocked</p>
                        <button onclick="completeUnlock()" class="btn-primary">
                            <i class="fas fa-eye mr-2"></i>View Full Details
                        </button>
                    </div>
                </div>
            `;
        }

        function completeUnlock() {
            hasUnlockedAddress = true;
            closePaymentModal();
            
            // Refresh the current modal with unlocked content
            if (currentPropertyId) {
                openPropertyDetails(currentPropertyId);
            }
            
            // Check if roommate modal is open
            if (document.getElementById('roommateDetailsModal').classList.contains('show')) {
                openRoommateDetails('rahul-sharma');
            }
        }

        // Contact Functions
        function contactViaWhatsApp(phone, propertyName) {
            const message = `Hi! I'm interested in ${propertyName}. Can we discuss the details?`;
            const whatsappUrl = `https://wa.me/${phone.replace(/\s+/g, '')}?text=${encodeURIComponent(message)}`;
            window.open(whatsappUrl, '_blank');
        }

        function contactViaCall(phone) {
            window.location.href = `tel:${phone}`;
        }

        function contactViaEmail(email, name) {
            const subject = `Interested in connecting as roommate`;
            const body = `Hi ${name},\n\nI found your profile on BluechipProperty and I'm interested in connecting as a potential roommate.\n\nBest regards`;
            window.location.href = `mailto:${email}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
        }

        // Modal Close Functions
        function closePropertyDetailsModal() {
            document.getElementById('propertyDetailsModal').classList.remove('show');
        }

        function closeRoommateDetailsModal() {
            document.getElementById('roommateDetailsModal').classList.remove('show');
        }

        // Filter functions for rentals page
        function toggleFurnishedFilter(element, status) {
            // Remove selected class from all radio items
            const radioItems = element.parentNode.querySelectorAll('.radio-item');
            radioItems.forEach(item => item.classList.remove('selected'));
            
            // Add selected class to clicked item
            element.classList.add('selected');
        }

        function toggleAmenityFilter(element, amenity) {
            element.classList.toggle('selected');
        }

        // List property page functions
        function selectFurnishedStatus(element, status) {
            // Remove selected class from all radio items
            const radioItems = element.parentNode.querySelectorAll('.radio-item');
            radioItems.forEach(item => item.classList.remove('selected'));
            
            // Add selected class to clicked item
            element.classList.add('selected');
        }

        function toggleAmenity(element, amenity) {
            element.classList.toggle('selected');
        }

        function handleListProperty(event) {
            event.preventDefault();
            alert('Property listed successfully!\n\nYour property has been submitted for review and will be live within 24 hours.\n\nThank you for choosing BluechipProperty!');
            
            // Reset form
            document.getElementById('listPropertyForm').reset();
            
            // Reset selected amenities and furnished status
            const selectedItems = document.querySelectorAll('.selected');
            selectedItems.forEach(item => item.classList.remove('selected'));
        }

        // Close modals when clicking outside
        window.onclick = function(event) {
            const signInModal = document.getElementById('signInModal');
            const forgotPasswordModal = document.getElementById('forgotPasswordModal');
            const propertyDetailsModal = document.getElementById('propertyDetailsModal');
            const roommateDetailsModal = document.getElementById('roommateDetailsModal');
            const paymentModal = document.getElementById('paymentModal');
            
            if (event.target === signInModal) {
                closeSignInModal();
            }
            if (event.target === forgotPasswordModal) {
                closeForgotPasswordModal();
            }
            if (event.target === propertyDetailsModal) {
                closePropertyDetailsModal();
            }
            if (event.target === roommateDetailsModal) {
                closeRoommateDetailsModal();
            }
            if (event.target === paymentModal) {
                closePaymentModal();
            }
        }
    </script>
</body>
</html>
