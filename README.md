<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dime Credit - Loyalty Credit Program</title>
  <style>
    :root {
      --primary-color: #0066cc;
      --secondary-color: #00aa88;
      --accent-color: #ff6633;
      --light-gray: #f5f5f5;
      --mid-gray: #e0e0e0;
      --dark-gray: #333333;
      --white: #ffffff;
      --shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    
    body {
      background-color: var(--light-gray);
      color: var(--dark-gray);
    }
    
    .app-container {
      max-width: 414px;
      height: 100vh;
      margin: 0 auto;
      background-color: var(--white);
      box-shadow: var(--shadow);
      position: relative;
      overflow: hidden;
    }
    
    header {
      background-color: var(--primary-color);
      color: var(--white);
      padding: 15px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    
    header h1 {
      font-size: 20px;
      font-weight: 600;
    }
    
    .tab-bar {
      display: flex;
      background-color: var(--white);
      border-bottom: 1px solid var(--mid-gray);
    }
    
    .tab {
      flex: 1;
      text-align: center;
      padding: 12px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .tab.active {
      color: var(--primary-color);
      border-bottom: 3px solid var(--primary-color);
      font-weight: 600;
    }
    
    .screen {
      display: none;
      height: calc(100vh - 118px);
      overflow-y: auto;
      padding: 15px;
    }
    
    .screen.active {
      display: block;
    }
    
    .card {
      background-color: var(--white);
      border-radius: 10px;
      box-shadow: var(--shadow);
      padding: 20px;
      margin-bottom: 15px;
    }
    
    .credit-card {
      background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
      color: var(--white);
      border-radius: 15px;
      padding: 25px;
      margin-bottom: 20px;
      position: relative;
      overflow: hidden;
    }
    
    .credit-card::before {
      content: "";
      position: absolute;
      width: 150px;
      height: 150px;
      border-radius: 50%;
      background-color: rgba(255, 255, 255, 0.1);
      top: -75px;
      right: -75px;
    }
    
    .credit-card::after {
      content: "";
      position: absolute;
      width: 100px;
      height: 100px;
      border-radius: 50%;
      background-color: rgba(255, 255, 255, 0.1);
      bottom: -50px;
      left: -50px;
    }
    
    .credit-limit {
      font-size: 28px;
      font-weight: 700;
      margin: 15px 0;
    }
    
    .credit-detail {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 8px 0;
    }
    
    .section-title {
      font-size: 18px;
      font-weight: 600;
      margin: 15px 0 10px;
    }
    
    .retailer-card {
      display: flex;
      align-items: center;
      padding: 15px;
      border-radius: 10px;
      background-color: var(--light-gray);
      margin-bottom: 10px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .retailer-logo {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background-color: var(--white);
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 15px;
      font-weight: bold;
      color: var(--primary-color);
    }
    
    .retailer-info {
      flex: 1;
    }
    
    .retailer-name {
      font-weight: 600;
    }
    
    .retailer-points {
      color: var(--secondary-color);
      font-size: 14px;
    }
    
    .transaction {
      display: flex;
      justify-content: space-between;
      border-bottom: 1px solid var(--mid-gray);
      padding: 12px 0;
    }
    
    .transaction:last-child {
      border-bottom: none;
    }
    
    .transaction-left {
      display: flex;
    }
    
    .transaction-icon {
      width: 36px;
      height: 36px;
      border-radius: 50%;
      background-color: var(--light-gray);
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 12px;
      font-weight: bold;
      color: var(--primary-color);
    }
    
    .transaction-info {
      flex: 1;
    }
    
    .transaction-title {
      font-weight: 600;
    }
    
    .transaction-date {
      font-size: 12px;
      color: #666;
    }
    
    .transaction-amount {
      text-align: right;
      font-weight: 600;
    }
    
    .transaction-status {
      font-size: 12px;
      color: var(--secondary-color);
      text-align: right;
    }
    
    .btn {
      background-color: var(--primary-color);
      color: var(--white);
      border: none;
      padding: 12px 20px;
      border-radius: 5px;
      font-weight: 600;
      cursor: pointer;
      width: 100%;
      margin-top: 10px;
    }
    
    .btn-outline {
      background-color: transparent;
      border: 2px solid var(--primary-color);
      color: var(--primary-color);
    }
    
    .loyalty-summary {
      display: flex;
      justify-content: space-between;
      margin-bottom: 15px;
    }
    
    .loyalty-metric {
      text-align: center;
      flex: 1;
      padding: 10px;
      border-right: 1px solid var(--mid-gray);
    }
    
    .loyalty-metric:last-child {
      border-right: none;
    }
    
    .metric-value {
      font-size: 22px;
      font-weight: 700;
      color: var(--primary-color);
    }
    
    .metric-label {
      font-size: 12px;
      color: #666;
    }
    
    .bottom-nav {
      position: fixed;
      bottom: 0;
      width: 100%;
      max-width: 414px;
      background-color: var(--white);
      display: flex;
      padding: 10px 0;
      border-top: 1px solid var(--mid-gray);
    }
    
    .nav-item {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      font-size: 12px;
      padding: 5px 0;
      color: #666;
      cursor: pointer;
    }
    
    .nav-item.active {
      color: var(--primary-color);
    }
    
    .nav-icon {
      font-size: 20px;
      margin-bottom: 4px;
    }
    
    .badge {
      display: inline-block;
      padding: 4px 8px;
      border-radius: 12px;
      font-size: 12px;
      font-weight: 600;
      margin-left: 5px;
    }
    
    .badge-primary {
      background-color: var(--primary-color);
      color: var(--white);
    }
    
    .badge-success {
      background-color: var(--secondary-color);
      color: var(--white);
    }
  </style>
</head>
<body>
  <div class="app-container">
    <header>
      <h1>Dime Credit</h1>
      <div style="font-size: 24px;">👤</div>
    </header>
    
    <div class="tab-bar">
      <div class="tab active" onclick="switchTab('home')">Home</div>
      <div class="tab" onclick="switchTab('credit')">Credit</div>
      <div class="tab" onclick="switchTab('loyalty')">Loyalty</div>
      <div class="tab" onclick="switchTab('activity')">Activity</div>
    </div>
    
    <!-- Home Screen -->
    <div id="home" class="screen active">
      <div class="credit-card">
        <div>Available Credit</div>
        <div class="credit-limit">Kes 2,500</div>
        <div class="credit-detail">
          <span>Credit Limit</span>
          <span>Kes 2,500</span>
        </div>
        <div class="credit-detail">
          <span>Due Date</span>
          <span>March 15, 2025</span>
        </div>
      </div>
      
      <div class="section-title">Connected Retailers</div>
      <div class="retailer-card">
        <div class="retailer-logo">Q</div>
        <div class="retailer-info">
          <div class="retailer-name">Quickmart</div>
          <div class="retailer-points">125 Points</div>
        </div>
        <div>
          <span class="badge badge-success">Active</span>
        </div>
      </div>
      
      <div class="retailer-card">
        <div class="retailer-logo">C</div>
        <div class="retailer-info">
          <div class="retailer-name">Carrefour</div>
          <div class="retailer-points">85 Points</div>
        </div>
        <div>
          <span class="badge badge-success">Active</span>
        </div>
      </div>
      
      <div class="retailer-card">
        <div class="retailer-logo">N</div>
        <div class="retailer-info">
          <div class="retailer-name">Naivas</div>
          <div class="retailer-points">Not connected</div>
        </div>
        <div>
          <button class="btn" style="margin: 0; padding: 5px 10px; font-size: 12px;">Connect</button>
        </div>
      </div>
      
      <div class="section-title">Recent Activity</div>
      <div class="card">
        <div class="transaction">
          <div class="transaction-left">
            <div class="transaction-icon">Q</div>
            <div class="transaction-info">
              <div class="transaction-title">Quickmart Purchase</div>
              <div class="transaction-date">Feb 26, 2025</div>
            </div>
          </div>
          <div>
            <div class="transaction-amount">Kes 850</div>
            <div class="transaction-status">+ 8 Points</div>
          </div>
        </div>
        
        <div class="transaction">
          <div class="transaction-left">
            <div class="transaction-icon">C</div>
            <div class="transaction-info">
              <div class="transaction-title">Carrefour Purchase</div>
              <div class="transaction-date">Feb 21, 2025</div>
            </div>
          </div>
          <div>
            <div class="transaction-amount">Kes 1,250</div>
            <div class="transaction-status">+ 12 Points</div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Credit Screen -->
    <div id="credit" class="screen">
      <div class="credit-card">
        <div>Available Credit</div>
        <div class="credit-limit">Kes 2,500</div>
        <div class="credit-detail">
          <span>Used Credit</span>
          <span>Kes 0</span>
        </div>
        <div class="credit-detail">
          <span>Interest Rate</span>
          <span>12% p.a.</span>
        </div>
      </div>
      
      <div class="card">
        <div class="section-title">Credit Details</div>
        <div class="credit-detail">
          <span>Credit Score</span>
          <span>720 <span class="badge badge-primary">Good</span></span>
        </div>
        <div class="credit-detail">
          <span>Last Adjusted</span>
          <span>Feb 15, 2025</span>
        </div>
        <div class="credit-detail">
          <span>Credit Basis</span>
          <span>Loyalty + Purchase History</span>
        </div>
      </div>
      
      <div class="card">
        <div class="section-title">Repayment Options</div>
        <div style="margin-bottom: 10px;">Select your preferred repayment method:</div>
        <div style="display: flex; margin-bottom: 15px;">
          <div style="flex: 1; text-align: center; padding: 10px; background-color: var(--light-gray); border-radius: 5px; margin-right: 5px;">
            <div style="font-weight: 600;">Auto-Deduct</div>
            <div style="font-size: 12px;">From future purchases</div>
          </div>
          <div style="flex: 1; text-align: center; padding: 10px; background-color: var(--primary-color); color: white; border-radius: 5px; margin-left: 5px;">
            <div style="font-weight: 600;">Mobile Money</div>
            <div style="font-size: 12px;">Direct payment</div>
          </div>
        </div>
        <button class="btn">Make A Payment</button>
      </div>
    </div>
    
    <!-- Loyalty Screen -->
    <div id="loyalty" class="screen">
      <div class="card">
        <div class="section-title">Your Loyalty Summary</div>
        <div class="loyalty-summary">
          <div class="loyalty-metric">
            <div class="metric-value">210</div>
            <div class="metric-label">Total Points</div>
          </div>
          <div class="loyalty-metric">
            <div class="metric-value">3</div>
            <div class="metric-label">Connected Stores</div>
          </div>
          <div class="loyalty-metric">
            <div class="metric-value">12</div>
            <div class="metric-label">Transactions</div>
          </div>
        </div>
        <div style="height: 200px; background-color: var(--light-gray); border-radius: 10px; display: flex; justify-content: center; align-items: center;">
          [Points Activity Graph]
        </div>
      </div>
      
      <div class="section-title">Connected Loyalty Programs</div>
      <div class="retailer-card">
        <div class="retailer-logo">Q</div>
        <div class="retailer-info">
          <div class="retailer-name">Quickmart Rewards</div>
          <div class="retailer-points">125 Points</div>
        </div>
        <div>
          <button class="btn btn-outline" style="margin: 0; padding: 5px 10px; font-size: 12px;">Use</button>
        </div>
      </div>
      
      <div class="retailer-card">
        <div class="retailer-logo">C</div>
        <div class="retailer-info">
          <div class="retailer-name">Carrefour Club</div>
          <div class="retailer-points">85 Points</div>
        </div>
        <div>
          <button class="btn btn-outline" style="margin: 0; padding: 5px 10px; font-size: 12px;">Use</button>
        </div>
      </div>
      
      <div class="card">
        <div class="section-title">Connect New Loyalty Program</div>
        <div style="margin-bottom: 15px;">Link your existing loyalty accounts to increase your credit limit.</div>
        <button class="btn">Find Retailers</button>
      </div>
    </div>
    
    <!-- Activity Screen -->
    <div id="activity" class="screen">
      <div class="section-title">Transaction History</div>
      <div class="card">
        <div class="transaction">
          <div class="transaction-left">
            <div class="transaction-icon">Q</div>
            <div class="transaction-info">
              <div class="transaction-title">Quickmart Purchase</div>
              <div class="transaction-date">Feb 26, 2025</div>
            </div>
          </div>
          <div>
            <div class="transaction-amount">Kes 850</div>
            <div class="transaction-status">+ 8 Points</div>
          </div>
        </div>
        
        <div class="transaction">
          <div class="transaction-left">
            <div class="transaction-icon">C</div>
            <div class="transaction-info">
              <div class="transaction-title">Carrefour Purchase</div>
              <div class="transaction-date">Feb 21, 2025</div>
            </div>
          </div>
          <div>
            <div class="transaction-amount">Kes 1,250</div>
            <div class="transaction-status">+ 12 Points</div>
          </div>
        </div>
        
        <div class="transaction">
          <div class="transaction-left">
            <div class="transaction-icon">Q</div>
            <div class="transaction-info">
              <div class="transaction-title">Quickmart Purchase</div>
              <div class="transaction-date">Feb 18, 2025</div>
            </div>
          </div>
          <div>
            <div class="transaction-amount">Kes 650</div>
            <div class="transaction-status">+ 6 Points</div>
          </div>
        </div>
        
        <div class="transaction">
          <div class="transaction-left">
            <div class="transaction-icon">C</div>
            <div class="transaction-info">
              <div class="transaction-title">Carrefour Purchase</div>
              <div class="transaction-date">Feb 15, 2025</div>
            </div>
          </div>
          <div>
            <div class="transaction-amount">Kes 950</div>
            <div class="transaction-status">+ 9 Points</div>
          </div>
        </div>
        
        <div class="transaction">
          <div class="transaction-left">
            <div class="transaction-icon">Q</div>
            <div class="transaction-info">
              <div class="transaction-title">Quickmart Purchase</div>
              <div class="transaction-date">Feb 10, 2025</div>
            </div>
          </div>
          <div>
            <div class="transaction-amount">Kes 1,050</div>
            <div class="transaction-status">+ 10 Points</div>
          </div>
        </div>
      </div>
      
      <div class="card">
        <div class="section-title">Credit Activity</div>
        <div style="text-align: center; padding: 20px 0;">
          <div style="font-size: 16px; color: #666;">No credit activity yet</div>
          <div style="font-size: 14px; margin-top: 5px;">Your credit usage and repayments will appear here</div>
        </div>
      </div>
    </div>
    
    <div class="bottom-nav">
      <div class="nav-item active">
        <div class="nav-icon">🏠</div>
        <div>Home</div>
      </div>
      <div class="nav-item">
        <div class="nav-icon">💳</div>
        <div>Credit</div>
      </div>
      <div class="nav-item">
        <div class="nav-icon">🛍️</div>
        <div>Shop</div>
      </div>
      <div class="nav-item">
        <div class="nav-icon">⚙️</div>
        <div>Settings</div>
      </div>
    </div>
  </div>
  
  <script>
    function switchTab(tabId) {
      // Hide all screens
      document.querySelectorAll('.screen').forEach(screen => {
        screen.classList.remove('active');
      });
      
      // Show selected screen
      document.getElementById(tabId).classList.add('active');
      
      // Update tab styles
      document.querySelectorAll('.tab').forEach(tab => {
        tab.classList.remove('active');
      });
      
      // Find the clicked tab and make it active
      const tabs = document.querySelectorAll('.tab');
      for (let i = 0; i < tabs.length; i++) {
        if (tabs[i].textContent.toLowerCase() === tabId.toLowerCase()) {
          tabs[i].classList.add('active');
          break;
        }
      }
    }
  </script>
</body>
</html>
