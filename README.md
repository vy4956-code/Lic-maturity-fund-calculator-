<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LIC Maturity Fund Calculator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            padding: 30px 0;
            background: linear-gradient(135deg, #1e5799 0%, #207cca 100%);
            color: white;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }
        
        header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        header p {
            font-size: 1.1rem;
            max-width: 700px;
            margin: 0 auto;
            opacity: 0.9;
        }
        
        .calculator-container {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 40px;
        }
        
        .input-section {
            flex: 1;
            min-width: 300px;
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
        }
        
        .result-section {
            flex: 1;
            min-width: 300px;
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #444;
        }
        
        input, select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 1rem;
            transition: border 0.3s;
        }
        
        input:focus, select:focus {
            border-color: #207cca;
            outline: none;
            box-shadow: 0 0 0 2px rgba(32, 124, 202, 0.2);
        }
        
        .btn {
            background: #207cca;
            color: white;
            border: none;
            padding: 14px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            width: 100%;
            transition: background 0.3s;
        }
        
        .btn:hover {
            background: #1a68b0;
        }
        
        .result-box {
            text-align: center;
            padding: 20px;
            background: #f8fafc;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        
        .result-title {
            font-size: 1.1rem;
            color: #666;
            margin-bottom: 10px;
        }
        
        .result-value {
            font-size: 2rem;
            font-weight: 700;
            color: #207cca;
        }
        
        .breakdown {
            margin-top: 20px;
        }
        
        .breakdown-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px solid #eee;
        }
        
        .breakdown-item:last-child {
            border-bottom: none;
            font-weight: 600;
            color: #207cca;
        }
        
        .info-section {
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
            margin-top: 30px;
        }
        
        .info-section h2 {
            color: #207cca;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #f0f0f0;
        }
        
        .info-points {
            list-style-type: none;
        }
        
        .info-points li {
            padding: 10px 0;
            padding-left: 30px;
            position: relative;
        }
        
        .info-points li:before {
            content: "•";
            color: #207cca;
            font-size: 1.5rem;
            position: absolute;
            left: 0;
            top: 5px;
        }
        
        footer {
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            color: #666;
            font-size: 0.9rem;
            border-top: 1px solid #eee;
        }
        
        @media (max-width: 768px) {
            .calculator-container {
                flex-direction: column;
            }
            
            header h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>LIC Maturity Fund Calculator</h1>
            <p>Estimate the maturity value of your LIC policy with our easy-to-use calculator</p>
        </header>
        
        <div class="calculator-container">
            <div class="input-section">
                <h2>Policy Details</h2>
                <div class="form-group">
                    <label for="policyType">Policy Type</label>
                    <select id="policyType">
                        <option value="endowment">Endowment Plan</option>
                        <option value="moneyBack">Money Back Plan</option>
                        <option value="wholeLife">Whole Life Plan</option>
                        <option value="ulip">ULIP</option>
                        <option value="term">Term Plan</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="sumAssured">Sum Assured (₹)</label>
                    <input type="number" id="sumAssured" placeholder="Enter sum assured amount" min="10000" value="500000">
                </div>
                
                <div class="form-group">
                    <label for="premiumAmount">Annual Premium (₹)</label>
                    <input type="number" id="premiumAmount" placeholder="Enter annual premium" min="1000" value="25000">
                </div>
                
                <div class="form-group">
                    <label for="policyTerm">Policy Term (Years)</label>
                    <input type="number" id="policyTerm" placeholder="Enter policy term" min="5" max="40" value="20">
                </div>
                
                <div class="form-group">
                    <label for="bonusRate">Bonus Rate (per 1000 sum assured)</label>
                    <input type="number" id="bonusRate" placeholder="Enter bonus rate" min="10" max="100" value="45" step="0.1">
                </div>
                
                <div class="form-group">
                    <label for="age">Your Current Age</label>
                    <input type="number" id="age" placeholder="Enter your age" min="18" max="65" value="30">
                </div>
                
                <button class="btn" id="calculateBtn">Calculate Maturity Value</button>
            </div>
            
            <div class="result-section">
                <h2>Maturity Estimate</h2>
                <div class="result-box">
                    <div class="result-title">Total Maturity Value</div>
                    <div class="result-value" id="maturityValue">₹ 0</div>
                </div>
                
                <div class="breakdown">
                    <div class="breakdown-item">
                        <span>Total Premiums Paid</span>
                        <span id="totalPremium">₹ 0</span>
                    </div>
                    <div class="breakdown-item">
                        <span>Total Bonus</span>
                        <span id="totalBonus">₹ 0</span>
                    </div>
                    <div class="breakdown-item">
                        <span>Final Bonus</span>
                        <span id="finalBonus">₹ 0</span>
                    </div>
                    <div class="breakdown-item">
                        <span>Total Maturity Value</span>
                        <span id="totalMaturity">₹ 0</span>
                    </div>
                </div>
                
                <div class="result-box" style="margin-top: 20px;">
                    <div class="result-title">Maturity Age</div>
                    <div class="result-value" id="maturityAge">0 years</div>
                </div>
            </div>
        </div>
        
        <div class="info-section">
            <h2>About LIC Maturity Calculator</h2>
            <ul class="info-points">
                <li>This calculator provides an estimate of your LIC policy's maturity value based on the information you provide.</li>
                <li>The actual maturity amount may vary based on the specific terms of your policy and LIC's declared bonus rates.</li>
                <li>Bonus rates are typically declared annually and may change over the policy term.</li>
                <li>Some policies may offer additional benefits like loyalty additions or terminal bonuses.</li>
                <li>For exact maturity values, please refer to your policy document or contact LIC directly.</li>
            </ul>
        </div>
        
        <footer>
            <p>Disclaimer: This calculator is for illustrative purposes only. The actual maturity value may vary based on the specific terms of your policy and LIC's declared bonus rates.</p>
            <p>© 2023 LIC Maturity Calculator. All rights reserved.</p>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const calculateBtn = document.getElementById('calculateBtn');
            
            calculateBtn.addEventListener('click', calculateMaturity);
            
            // Calculate on page load
            calculateMaturity();
            
            function calculateMaturity() {
                // Get input values
                const sumAssured = parseFloat(document.getElementById('sumAssured').value) || 0;
                const premiumAmount = parseFloat(document.getElementById('premiumAmount').value) || 0;
                const policyTerm = parseFloat(document.getElementById('policyTerm').value) || 0;
                const bonusRate = parseFloat(document.getElementById('bonusRate').value) || 0;
                const age = parseFloat(document.getElementById('age').value) || 0;
                
                // Calculate components
                const totalPremium = premiumAmount * policyTerm;
                
                // Calculate bonus (simplified calculation)
                const annualBonus = (sumAssured / 1000) * bonusRate;
                const totalBonus = annualBonus * policyTerm;
                
                // Calculate final bonus (typically a percentage of sum assured)
                const finalBonus = sumAssured * 0.05; // Assuming 5% of sum assured
                
                // Calculate total maturity value
                const totalMaturity = sumAssured + totalBonus + finalBonus;
                
                // Calculate maturity age
                const maturityAge = age + policyTerm;
                
                // Format numbers with Indian numbering system
                const formatter = new Intl.NumberFormat('en-IN', {
                    maximumFractionDigits: 0
                });
                
                // Update the UI
                document.getElementById('maturityValue').textContent = '₹ ' + formatter.format(totalMaturity);
                document.getElementById('totalPremium').textContent = '₹ ' + formatter.format(totalPremium);
                document.getElementById('totalBonus').textContent = '₹ ' + formatter.format(totalBonus);
                document.getElementById('finalBonus').textContent = '₹ ' + formatter.format(finalBonus);
                document.getElementById('totalMaturity').textContent = '₹ ' + formatter.format(totalMaturity);
                document.getElementById('maturityAge').textContent = maturityAge + ' years';
            }
        });
    </script>
</body>
</html>
