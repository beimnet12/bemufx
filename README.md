<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BEMUFX | Professional Trading Journal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #0f172a;
            --primary-dark: #020617;
            --secondary: #3b82f6;
            --secondary-dark: #1d4ed8;
            --success: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --info: #06b6d4;
            --light: #f8fafc;
            --dark: #1e293b;
            --gray-100: #f1f5f9;
            --gray-200: #e2e8f0;
            --gray-300: #cbd5e1;
            --gray-700: #334155;
            --gray-900: #0f172a;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f0f4f8 0%, #d9e2ec 100%);
            color: var(--dark);
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header */
        header {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            box-shadow: 0 4px 20px rgba(0,0,0,0.15);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.8rem;
            font-weight: 800;
        }
        
        .logo-icon {
            background: var(--secondary);
            width: 40px;
            height: 40px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .logo-text {
            background: linear-gradient(90deg, #60a5fa, #3b82f6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 900;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }
        
        nav a {
            text-decoration: none;
            color: rgba(255,255,255,0.9);
            font-weight: 500;
            transition: all 0.3s;
            padding: 0.5rem 0;
            position: relative;
        }
        
        nav a:hover {
            color: white;
        }
        
        nav a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--secondary);
            transition: width 0.3s;
        }
        
        nav a:hover::after {
            width: 100%;
        }
        
        .user-menu {
            display: flex;
            align-items: center;
            gap: 1rem;
            position: relative;
        }
        
        .user-avatar {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            cursor: pointer;
        }
        
        .dropdown-menu {
            display: none;
            position: absolute;
            top: 100%;
            right: 0;
            background: white;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
            min-width: 200px;
            z-index: 1001;
            margin-top: 10px;
        }
        
        .dropdown-menu.show {
            display: block;
        }
        
        .dropdown-item {
            padding: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
            text-decoration: none;
            color: var(--gray-900);
            transition: all 0.3s;
            border-bottom: 1px solid var(--gray-100);
        }
        
        .dropdown-item:last-child {
            border-bottom: none;
        }
        
        .dropdown-item:hover {
            background: var(--gray-100);
            color: var(--secondary);
        }
        
        /* Buttons */
        .btn {
            padding: 0.7rem 1.8rem;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            border: none;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-size: 0.95rem;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--secondary) 0%, var(--secondary-dark) 100%);
            color: white;
            box-shadow: 0 4px 12px rgba(59, 130, 246, 0.3);
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 16px rgba(59, 130, 246, 0.4);
        }
        
        .btn-outline {
            background: transparent;
            color: var(--secondary);
            border: 2px solid var(--secondary);
        }
        
        .btn-outline:hover {
            background: var(--secondary);
            color: white;
        }
        
        .btn-danger {
            background: var(--danger);
            color: white;
        }
        
        .btn-danger:hover {
            background: #dc2626;
        }
        
        /* Main Layout */
        .dashboard {
            display: grid;
            grid-template-columns: 280px 1fr;
            gap: 2rem;
            padding: 2rem 0;
            min-height: calc(100vh - 80px);
        }
        
        /* Sidebar */
        .sidebar {
            background: white;
            border-radius: 16px;
            padding: 1.5rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
            height: fit-content;
            position: sticky;
            top: 100px;
        }
        
        .sidebar-section {
            margin-bottom: 2rem;
        }
        
        .sidebar-section h3 {
            color: var(--primary);
            margin-bottom: 1rem;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .sidebar-nav {
            list-style: none;
        }
        
        .sidebar-nav li {
            margin-bottom: 0.5rem;
        }
        
        .sidebar-nav a {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 0.8rem 1rem;
            text-decoration: none;
            color: var(--gray-700);
            border-radius: 10px;
            transition: all 0.3s;
        }
        
        .sidebar-nav a:hover {
            background: var(--gray-100);
            color: var(--primary);
        }
        
        .sidebar-nav a.active {
            background: linear-gradient(135deg, rgba(59, 130, 246, 0.1) 0%, rgba(29, 78, 216, 0.1) 100%);
            color: var(--secondary-dark);
            font-weight: 600;
        }
        
        /* Stats Cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .stat-card {
            background: white;
            padding: 1.5rem;
            border-radius: 16px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
            transition: transform 0.3s;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
        }
        
        .stat-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }
        
        .icon-success { background: rgba(16, 185, 129, 0.1); color: var(--success); }
        .icon-danger { background: rgba(239, 68, 68, 0.1); color: var(--danger); }
        .icon-warning { background: rgba(245, 158, 11, 0.1); color: var(--warning); }
        .icon-info { background: rgba(6, 182, 212, 0.1); color: var(--info); }
        
        .stat-value {
            font-size: 2rem;
            font-weight: 800;
            color: var(--primary);
            margin: 0.5rem 0;
        }
        
        /* Trade List */
        .trades-list {
            background: white;
            border-radius: 16px;
            padding: 2rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        }
        
        .trade-item {
            border: 2px solid var(--gray-100);
            border-radius: 12px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            transition: all 0.3s;
            position: relative;
        }
        
        .trade-item:hover {
            border-color: var(--secondary);
            box-shadow: 0 4px 12px rgba(59, 130, 246, 0.1);
        }
        
        .trade-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            padding-bottom: 1rem;
            border-bottom: 2px solid var(--gray-100);
        }
        
        .trade-pair {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--primary);
        }
        
        .trade-direction {
            padding: 0.3rem 1rem;
            border-radius: 20px;
            font-weight: 600;
            font-size: 0.9rem;
        }
        
        .direction-long { background: rgba(16, 185, 129, 0.15); color: var(--success); }
        .direction-short { background: rgba(239, 68, 68, 0.15); color: var(--danger); }
        
        .trade-profit {
            font-size: 1.5rem;
            font-weight: 800;
        }
        
        .profit-positive { color: var(--success); }
        .profit-negative { color: var(--danger); }
        .profit-neutral { color: var(--gray-700); }
        
        .trade-meta {
            display: flex;
            gap: 2rem;
            margin: 1rem 0;
            font-size: 0.9rem;
            color: var(--gray-700);
        }
        
        .meta-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        /* Calendar */
        .calendar-container {
            background: white;
            border-radius: 16px;
            padding: 2rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
            margin-bottom: 2rem;
        }
        
        .calendar-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 5px;
        }
        
        .calendar-day {
            padding: 10px;
            text-align: center;
            font-weight: bold;
            color: var(--gray-700);
        }
        
        .calendar-date {
            padding: 15px 10px;
            text-align: center;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
        }
        
        .calendar-date:hover {
            background: var(--gray-100);
        }
        
        .calendar-date.today {
            background: var(--secondary);
            color: white;
        }
        
        .calendar-date.has-trades {
            background: rgba(16, 185, 129, 0.1);
            border: 2px solid var(--success);
        }
        
        .calendar-date.has-losses {
            background: rgba(239, 68, 68, 0.1);
            border: 2px solid var(--danger);
        }
        
        .date-profit {
            font-size: 0.7rem;
            font-weight: bold;
            margin-top: 5px;
        }
        
        .date-profit.positive { color: var(--success); }
        .date-profit.negative { color: var(--danger); }
        
        /* Analytics Charts */
        .charts-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .chart-card {
            background: white;
            border-radius: 16px;
            padding: 1.5rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        }
        
        .chart-card h3 {
            margin-bottom: 1rem;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        /* Trading Gallery */
        .gallery-container {
            background: white;
            border-radius: 16px;
            padding: 2rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        }
        
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .gallery-item {
            border: 2px solid var(--gray-200);
            border-radius: 12px;
            padding: 1rem;
            transition: all 0.3s;
        }
        
        .gallery-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            border-color: var(--secondary);
        }
        
        /* Profile Page */
        .profile-container {
            background: white;
            border-radius: 16px;
            padding: 2rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        }
        
        .profile-header {
            display: flex;
            align-items: center;
            gap: 2rem;
            margin-bottom: 2rem;
        }
        
        .profile-avatar {
            width: 100px;
            height: 100px;
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2.5rem;
            font-weight: bold;
        }
        
        .profile-info h2 {
            color: var(--primary);
            margin-bottom: 0.5rem;
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            backdrop-filter: blur(4px);
        }
        
        .modal-content {
            background: white;
            border-radius: 20px;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            animation: modalSlide 0.3s ease;
        }
        
        @keyframes modalSlide {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        .modal-header {
            padding: 2rem 2rem 1rem;
            border-bottom: 2px solid var(--gray-100);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-body {
            padding: 2rem;
        }
        
        .modal-footer {
            padding: 1rem 2rem 2rem;
            border-top: 2px solid var(--gray-100);
            display: flex;
            gap: 1rem;
            justify-content: flex-end;
        }
        
        /* Form Styles */
        .form-section {
            margin-bottom: 2rem;
            padding-bottom: 2rem;
            border-bottom: 2px solid var(--gray-100);
        }
        
        .form-section:last-child {
            border-bottom: none;
            margin-bottom: 0;
            padding-bottom: 0;
        }
        
        .form-section-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 1.5rem;
        }
        
        .form-section-header h3 {
            color: var(--primary);
            font-size: 1.3rem;
        }
        
        .section-icon {
            width: 40px;
            height: 40px;
            background: var(--secondary);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
        }
        
        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--gray-900);
            font-size: 0.95rem;
        }
        
        .form-group .label-hint {
            font-size: 0.85rem;
            color: var(--gray-700);
            font-weight: normal;
            margin-top: 0.3rem;
        }
        
        .form-control {
            width: 100%;
            padding: 0.8rem 1rem;
            border: 2px solid var(--gray-200);
            border-radius: 10px;
            font-size: 1rem;
            transition: all 0.3s;
            background: white;
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--secondary);
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }
        
        .radio-group {
            display: flex;
            gap: 2rem;
        }
        
        .radio-option {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
        }
        
        .radio-option input[type="radio"] {
            accent-color: var(--secondary);
        }
        
        .tag-input {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            padding: 0.5rem;
            border: 2px solid var(--gray-200);
            border-radius: 10px;
            min-height: 52px;
        }
        
        .tag {
            background: var(--gray-100);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.85rem;
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }
        
        .tag-remove {
            background: none;
            border: none;
            color: var(--gray-700);
            cursor: pointer;
            font-size: 0.8rem;
        }
        
        .tag-input input {
            border: none;
            outline: none;
            flex: 1;
            min-width: 100px;
            padding: 0.5rem;
        }
        
        /* Emotion Sliders */
        .emotion-slider {
            margin: 1rem 0;
        }
        
        .slider-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
        }
        
        .slider-container {
            background: var(--gray-100);
            height: 10px;
            border-radius: 5px;
            position: relative;
        }
        
        .slider-value {
            position: absolute;
            height: 100%;
            background: var(--secondary);
            border-radius: 5px;
        }
        
        .slider-marks {
            display: flex;
            justify-content: space-between;
            margin-top: 0.5rem;
            font-size: 0.8rem;
            color: var(--gray-700);
        }
        
        /* Auth Pages */
        .auth-container {
            display: flex;
            min-height: 100vh;
        }
        
        .auth-left {
            flex: 1;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            padding: 4rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .auth-right {
            flex: 1;
            background: white;
            padding: 4rem;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .auth-form {
            max-width: 400px;
            margin: 0 auto;
            width: 100%;
        }
        
        .auth-form h2 {
            margin-bottom: 2rem;
            color: var(--primary);
        }
        
        /* Responsive */
        @media (max-width: 1024px) {
            .dashboard {
                grid-template-columns: 1fr;
            }
            
            .sidebar {
                position: static;
                margin-bottom: 2rem;
            }
        }
        
        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                gap: 1rem;
                text-align: center;
            }
            
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .auth-container {
                flex-direction: column;
            }
            
            .auth-left, .auth-right {
                padding: 2rem;
            }
            
            .form-grid {
                grid-template-columns: 1fr;
            }
            
            .calendar-grid {
                grid-template-columns: repeat(7, 1fr);
                font-size: 0.8rem;
            }
            
            .calendar-date {
                padding: 8px 5px;
            }
        }
    </style>
</head>
<body>
    <!-- Main Dashboard -->
    <div id="dashboardView" style="display: none;">
        <header>
            <div class="container header-container">
                <div class="logo">
                    <div class="logo-icon">
                        <i class="fas fa-chart-candlestick"></i>
                    </div>
                    <span class="logo-text">BEMUFX</span>
                </div>
                
                <nav>
                    <ul>
                        <li><a href="#" onclick="showPage('dashboard')"><i class="fas fa-home"></i> Dashboard</a></li>
                        <li><a href="#" onclick="showPage('journal')"><i class="fas fa-book"></i> Journal</a></li>
                        <li><a href="#" onclick="showPage('analytics')"><i class="fas fa-chart-line"></i> Analytics</a></li>
                        <li><a href="#" onclick="showPage('reports')"><i class="fas fa-chart-pie"></i> Reports</a></li>
                        <li><a href="#" onclick="showPage('community')"><i class="fas fa-users"></i> Community</a></li>
                        <li><a href="#" onclick="showPage('gallery')"><i class="fas fa-images"></i> Gallery</a></li>
                    </ul>
                </nav>
                
                <div class="user-menu">
                    <button class="btn btn-primary" onclick="showAddTradeModal()">
                        <i class="fas fa-plus"></i> New Trade
                    </button>
                    <div class="user-avatar" onclick="toggleUserMenu()">
                        <span id="userInitial">U</span>
                    </div>
                    <div class="dropdown-menu" id="userDropdown">
                        <a href="#" class="dropdown-item" onclick="showPage('profile')">
                            <i class="fas fa-user"></i> Profile
                        </a>
                        <a href="#" class="dropdown-item" onclick="showPage('settings')">
                            <i class="fas fa-cog"></i> Settings
                        </a>
                        <a href="#" class="dropdown-item" onclick="logout()">
                            <i class="fas fa-sign-out-alt"></i> Logout
                        </a>
                    </div>
                </div>
            </div>
        </header>

        <div class="container">
            <!-- Dashboard Page -->
            <div id="pageDashboard" class="dashboard">
                <!-- Sidebar -->
                <aside class="sidebar">
                    <div class="sidebar-section">
                        <h3><i class="fas fa-chart-simple"></i> Quick Stats</h3>
                        <div class="sidebar-nav">
                            <li><a href="#" onclick="filterTrades('today')"><i class="fas fa-fire"></i> Today's Trades</a></li>
                            <li><a href="#" onclick="filterTrades('week')"><i class="fas fa-calendar-week"></i> This Week</a></li>
                            <li><a href="#" onclick="filterTrades('month')"><i class="fas fa-calendar-alt"></i> This Month</a></li>
                            <li><a href="#" onclick="filterTrades('best')"><i class="fas fa-trophy"></i> Best Trades</a></li>
                        </div>
                    </div>
                    
                    <div class="sidebar-section">
                        <h3><i class="fas fa-filter"></i> Filters</h3>
                        <div class="form-group">
                            <label>Instrument Type</label>
                            <select class="form-control" id="filterInstrument" onchange="filterTrades()">
                                <option value="all">All Instruments</option>
                                <option value="forex">Forex</option>
                                <option value="stocks">Stocks</option>
                                <option value="crypto">Crypto</option>
                                <option value="indices">Indices</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label>Timeframe</label>
                            <select class="form-control" id="filterTimeframe" onchange="filterTrades()">
                                <option value="all">All Time</option>
                                <option value="today">Today</option>
                                <option value="week">This Week</option>
                                <option value="month">This Month</option>
                                <option value="3months">Last 3 Months</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label>Result</label>
                            <select class="form-control" id="filterResult" onchange="filterTrades()">
                                <option value="all">All Results</option>
                                <option value="win">Winners Only</option>
                                <option value="loss">Losers Only</option>
                                <option value="break-even">Break Even</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="sidebar-section">
                        <h3><i class="fas fa-tags"></i> Popular Tags</h3>
                        <div class="tags-container" id="popularTags">
                            <!-- Tags will be loaded here -->
                        </div>
                    </div>
                </aside>

                <!-- Main Content Area -->
                <main>
                    <!-- Stats -->
                    <div class="stats-grid" id="statsGrid">
                        <!-- Stats will be loaded here -->
                    </div>

                    <!-- Calendar View -->
                    <div class="calendar-container" id="calendarContainer">
                        <div class="calendar-header">
                            <h2><i class="far fa-calendar"></i> Trading Calendar</h2>
                            <div>
                                <button class="btn btn-outline" onclick="changeMonth(-1)">
                                    <i class="fas fa-chevron-left"></i>
                                </button>
                                <span id="currentMonth" style="margin: 0 1rem; font-weight: bold;"></span>
                                <button class="btn btn-outline" onclick="changeMonth(1)">
                                    <i class="fas fa-chevron-right"></i>
                                </button>
                            </div>
                        </div>
                        <div class="calendar-grid" id="calendarGrid">
                            <!-- Calendar will be loaded here -->
                        </div>
                    </div>

                    <!-- Recent Trades -->
                    <div class="trades-list">
                        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 2rem;">
                            <h2 style="color: var(--primary);"><i class="fas fa-history"></i> Recent Trades</h2>
                            <button class="btn btn-primary" onclick="showAddTradeModal()">
                                <i class="fas fa-plus"></i> Add New Trade
                            </button>
                        </div>
                        
                        <div id="tradesContainer">
                            <!-- Trades will be loaded here -->
                        </div>
                    </div>
                </main>
            </div>

            <!-- Journal Page -->
            <div id="pageJournal" class="dashboard" style="display: none;">
                <main style="grid-column: 1 / -1;">
                    <div class="trades-list">
                        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 2rem;">
                            <h2 style="color: var(--primary);"><i class="fas fa-book"></i> Trading Journal</h2>
                            <div>
                                <button class="btn btn-outline" onclick="exportTrades()">
                                    <i class="fas fa-download"></i> Export
                                </button>
                                <button class="btn btn-primary" onclick="showAddTradeModal()">
                                    <i class="fas fa-plus"></i> Add Trade
                                </button>
                            </div>
                        </div>
                        
                        <div id="journalTradesContainer">
                            <!-- Journal trades will be loaded here -->
                        </div>
                    </div>
                </main>
            </div>

            <!-- Analytics Page -->
            <div id="pageAnalytics" class="dashboard" style="display: none;">
                <main style="grid-column: 1 / -1;">
                    <div class="charts-container">
                        <div class="chart-card">
                            <h3><i class="fas fa-chart-bar"></i> Win Rate Over Time</h3>
                            <div id="winRateChart" style="height: 300px; display: flex; align-items: center; justify-content: center; color: var(--gray-700);">
                                Chart will be displayed here
                            </div>
                        </div>
                        <div class="chart-card">
                            <h3><i class="fas fa-balance-scale"></i> Risk/Reward Distribution</h3>
                            <div id="riskRewardChart" style="height: 300px; display: flex; align-items: center; justify-content: center; color: var(--gray-700);">
                                Chart will be displayed here
                            </div>
                        </div>
                        <div class="chart-card">
                            <h3><i class="fas fa-brain"></i> Emotion Score Trend</h3>
                            <div id="emotionChart" style="height: 300px; display: flex; align-items: center; justify-content: center; color: var(--gray-700);">
                                Chart will be displayed here
                            </div>
                        </div>
                        <div class="chart-card">
                            <h3><i class="fas fa-coins"></i> Profit by Instrument</h3>
                            <div id="instrumentChart" style="height: 300px; display: flex; align-items: center; justify-content: center; color: var(--gray-700);">
                                Chart will be displayed here
                            </div>
                        </div>
                    </div>
                </main>
            </div>

            <!-- Reports Page -->
            <div id="pageReports" class="dashboard" style="display: none;">
                <main style="grid-column: 1 / -1;">
                    <div class="trades-list">
                        <h2 style="color: var(--primary); margin-bottom: 2rem;"><i class="fas fa-chart-pie"></i> Performance Reports</h2>
                        
                        <div class="charts-container">
                            <div class="chart-card">
                                <h3><i class="fas fa-file-alt"></i> Monthly Report</h3>
                                <div id="monthlyReport" style="min-height: 200px;">
                                    <!-- Monthly report will be generated here -->
                                </div>
                            </div>
                            <div class="chart-card">
                                <h3><i class="fas fa-file-alt"></i> Weekly Report</h3>
                                <div id="weeklyReport" style="min-height: 200px;">
                                    <!-- Weekly report will be generated here -->
                                </div>
                            </div>
                        </div>
                        
                        <div style="margin-top: 2rem;">
                            <button class="btn btn-primary" onclick="generateReport('pdf')">
                                <i class="fas fa-file-pdf"></i> Export as PDF
                            </button>
                            <button class="btn btn-outline" onclick="generateReport('csv')">
                                <i class="fas fa-file-csv"></i> Export as CSV
                            </button>
                        </div>
                    </div>
                </main>
            </div>

            <!-- Community Page -->
            <div id="pageCommunity" class="dashboard" style="display: none;">
                <main style="grid-column: 1 / -1;">
                    <div class="trades-list">
                        <h2 style="color: var(--primary); margin-bottom: 2rem;"><i class="fas fa-users"></i> Trading Community</h2>
                        
                        <div class="charts-container">
                            <div class="chart-card">
                                <h3><i class="fas fa-trophy"></i> Top Traders This Month</h3>
                                <div id="topTraders" style="min-height: 200px;">
                                    <p>Community features coming soon!</p>
                                </div>
                            </div>
                            <div class="chart-card">
                                <h3><i class="fas fa-comments"></i> Recent Discussions</h3>
                                <div id="recentDiscussions" style="min-height: 200px;">
                                    <p>Join our community to discuss trading strategies!</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </main>
            </div>

            <!-- Gallery Page -->
            <div id="pageGallery" class="dashboard" style="display: none;">
                <main style="grid-column: 1 / -# bemufx
