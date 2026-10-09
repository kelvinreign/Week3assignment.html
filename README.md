<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pricing Table</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background-color: #0f172a;
      color: #f8fafc;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 3rem 1rem;
    }

    .container {
      max-width: 1200px;
      width: 100%;
      margin: 0 auto;
    }

    .header {
      text-align: center;
      margin-bottom: 3.5rem;
    }

    .badge {
      background-color: rgba(99, 102, 241, 0.15);
      color: #818cf8;
      padding: 0.35rem 1rem;
      border-radius: 9999px;
      font-size: 0.875rem;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.05em;
      display: inline-block;
      margin-bottom: 1rem;
      border: 1px solid rgba(99, 102, 241, 0.3);
    }

    .header h1 {
      font-size: 2.75rem;
      font-weight: 800;
      margin-bottom: 1rem;
      background: linear-gradient(135deg, #ffffff 0%, #cbd5e1 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .header p {
      color: #94a3b8;
      font-size: 1.125rem;
      max-width: 600px;
      margin: 0 auto 2rem auto;
    }

    .toggle-container {
      display: inline-flex;
      align-items: center;
      background-color: #1e293b;
      padding: 0.5rem 1.25rem;
      border-radius: 9999px;
      border: 1px solid #334155;
      gap: 1rem;
    }

    .toggle-label {
      font-weight: 600;
      font-size: 0.95rem;
      color: #64748b;
      transition: color 0.3s ease;
    }

    .toggle-label.active {
      color: #ffffff;
    }

    .discount-pill {
      background-color: #10b981;
      color: #ffffff;
      font-size: 0.75rem;
      padding: 0.15rem 0.5rem;
      border-radius: 9999px;
      margin-left: 0.25rem;
    }

    .switch {
      position: relative;
      display: inline-block;
      width: 50px;
      height: 26px;
    }

    .switch input {
      opacity: 0;
      width: 0;
      height: 0;
    }

    .slider {
      position: absolute;
      cursor: pointer;
      top: 0; left: 0; right: 0; bottom: 0;
      background-color: #334155;
      transition: 0.3s;
      border-radius: 34px;
    }

    .slider:before {
      position: absolute;
      content: "";
      height: 20px;
      width: 20px;
      left: 3px;
      bottom: 3px;
      background-color: white;
      transition: 0.3s;
      border-radius: 50%;
    }

    input:checked + .slider {
      background-color: #6366f1;
    }

    input:checked + .slider:before {
      transform: translateX(24px);
    }

    .pricing-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2rem;
      align-items: stretch;
    }

    .card {
      background-color: #1e293b;
      border: 2px solid #334155;
      border-radius: 1.25rem;
      padding: 2rem;
      position: relative;
      cursor: pointer;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
      display: grid;
      grid-template-rows: auto auto 1fr auto;
      gap: 1.5rem;
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: #475569;
    }

    .card.featured {
      background-color: #1e1b4b;
      border-color: #6366f1;
      box-shadow: 0 20px 25px -5px rgba(99, 102, 241, 0.2);
    }

    .popular-badge {
      position: absolute;
      top: -14px;
      left: 50%;
      transform: translateX(-50%);
      background: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
      color: #ffffff;
      padding: 0.25rem 1rem;
      border-radius: 9999px;
      font-size: 0.8rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }

    .card.selected {
      border-color: #10b981;
      box-shadow: 0 0 0 4px rgba(16, 185, 129, 0.25);
    }

    .card-section {
      width: 100%;
    }

    .card-header {
      min-height: 80px;
    }

    .plan-title {
      font-size: 1.5rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
    }

    .plan-desc {
      color: #94a3b8;
      font-size: 0.875rem;
      line-height: 1.4;
    }

    .card-price {
      min-height: 70px;
      border-bottom: 1px solid #334155;
      padding-bottom: 1.25rem;
    }

    .price-wrapper {
      display: flex;
      align-items: baseline;
      gap: 0.25rem;
    }

    .currency {
      font-size: 1.5rem;
      font-weight: 600;
      color: #94a3b8;
    }

    .amount {
      font-size: 3rem;
      font-weight: 800;
      color: #ffffff;
    }

    .period {
      color: #94a3b8;
      font-size: 0.95rem;
    }

    .billing-note {
      font-size: 0.75rem;
      color: #64748b;
      margin-top: 0.25rem;
    }

    .card-features {
      display: flex;
      flex-direction: column;
    }

    .features-title {
      font-size: 0.85rem;
      font-weight: 600;
      color: #cbd5e1;
      margin-bottom: 1rem;
    }

    .card-features ul {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.85rem;
    }

    .card-features li {
      font-size: 0.9rem;
      color: #cbd5e1;
      display: flex;
      align-items: center;
      gap: 0.6rem;
    }

    .card-features li.disabled {
      color: #475569;
    }

    .icon {
      font-weight: bold;
    }

    .icon.check {
      color: #10b981;
    }

    .icon.cross {
      color: #64748b;
    }

    .card-action {
      align-self: end;
    }

    .btn {
      width: 100%;
      padding: 0.85rem;
      border-radius: 0.75rem;
      font-weight: 600;
      font-size: 0.95rem;
      cursor: pointer;
      border: none;
      transition: all 0.2s ease;
    }

    .btn-secondary {
      background-color: #334155;
      color: #ffffff;
    }

    .btn-secondary:hover {
      background-color: #475569;
    }

    .btn-primary {
      background: linear-gradient(135deg, #6366f1 0%, #4f46e5 100%);
      color: #ffffff;
    }

    .btn-primary:hover {
      opacity: 0.9;
    }

    .btn.selected-btn {
      background-color: #10b981 !important;
      color: #ffffff !important;
    }

    @media (max-width: 960px) {
      .pricing-grid {
        grid-template-columns: 1fr;
        max-width: 450px;
        margin: 0 auto;
      }

      .card.featured {
        order: -1;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <header class="header">
      <span class="badge">Flexible Plans</span>
      <h1>Simple, Transparent Pricing</h1>
      <p>Choose the perfect plan for your growing business. Upgrade or cancel anytime.</p>

      <div class="toggle-container">
        <span id="monthly-label" class="toggle-label active">Monthly</span>
        <label class="switch">
          <input type="checkbox" id="billing-toggle" />
          <span class="slider"></span>
        </label>
        <span id="annual-label" class="toggle-label">
          Annual <span class="discount-pill">Save 20%</span>
        </span>
      </div>
    </header>

    <div class="pricing-grid">
      <div class="card" id="card-starter" onclick="selectCard('starter')">
        <div class="card-section card-header">
          <h2 class="plan-title">Starter</h2>
          <p class="plan-desc">Perfect for freelancers and small side projects getting started.</p>
        </div>

        <div class="card-section card-price">
          <div class="price-wrapper">
            <span class="currency">$</span>
            <span class="amount" data-monthly="15" data-annual="12">15</span>
            <span class="period">/month</span>
          </div>
          <p class="billing-note" id="note-starter">Billed monthly</p>
        </div>

        <div class="card-section card-features">
          <span class="features-title">Includes:</span>
          <ul>
            <li><span class="icon check">✓</span> Up to 5 projects</li>
            <li><span class="icon check">✓</span> Basic analytics dashboard</li>
            <li><span class="icon check">✓</span> 24/7 Community support</li>
            <li><span class="icon check">✓</span> 5GB Cloud storage</li>
            <li class="disabled"><span class="icon cross">✕</span> Custom domain integration</li>
            <li class="disabled"><span class="icon cross">✕</span> Advanced security & SSL</li>
          </ul>
        </div>

        <div class="card-section card-action">
          <button class="btn btn-secondary" onclick="handleSelect('starter', event)">Select Starter</button>
        </div>
      </div>

      <div class="card featured" id="card-pro" onclick="selectCard('pro')">
        <div class="popular-badge">Most Popular</div>

        <div class="card-section card-header">
          <h2 class="plan-title">Pro</h2>
          <p class="plan-desc">Ideal for expanding teams and scaling digital products fast.</p>
        </div>

        <div class="card-section card-price">
          <div class="price-wrapper">
            <span class="currency">$</span>
            <span class="amount" data-monthly="49" data-annual="39">49</span>
            <span class="period">/month</span>
          </div>
          <p class="billing-note" id="note-pro">Billed monthly</p>
        </div>

        <div class="card-section card-features">
          <span class="features-title">Everything in Starter, plus:</span>
          <ul>
            <li><span class="icon check">✓</span> Unlimited projects</li>
            <li><span class="icon check">✓</span> Advanced real-time analytics</li>
            <li><span class="icon check">✓</span> Priority email & chat support</li>
            <li><span class="icon check">✓</span> 100GB Cloud storage</li>
            <li><span class="icon check">✓</span> Custom domain integration</li>
            <li class="disabled"><span class="icon cross">✕</span> Dedicated account manager</li>
          </ul>
        </div>

        <div class="card-section card-action">
          <button class="btn btn-primary" onclick="handleSelect('pro', event)">Select Pro</button>
        </div>
      </div>

      <div class="card" id="card-enterprise" onclick="selectCard('enterprise')">
        <div class="card-section card-header">
          <h2 class="plan-title">Enterprise</h2>
          <p class="plan-desc">Tailored infrastructure and dedicated support for large organizations.</p>
        </div>

        <div class="card-section card-price">
          <div class="price-wrapper">
            <span class="currency">$</span>
            <span class="amount" data-monthly="129" data-annual="99">129</span>
            <span class="period">/month</span>
          </div>
          <p class="billing-note" id="note-enterprise">Billed monthly</p>
        </div>

        <div class="card-section card-features">
          <span class="features-title">Everything in Pro, plus:</span>
          <ul>
            <li><span class="icon check">✓</span> Unlimited team seats</li>
            <li><span class="icon check">✓</span> Dedicated account manager</li>
            <li><span class="icon check">✓</span> 99.9% Uptime SLA guarantee</li>
            <li><span class="icon check">✓</span> Custom API integrations</li>
            <li><span class="icon check">✓</span> 1TB Cloud storage</li>
            <li><span class="icon check">✓</span> Enterprise SOC2 Security</li>
          </ul>
        </div>

        <div class="card-section card-action">
          <button class="btn btn-secondary" onclick="handleSelect('enterprise', event)">Select Enterprise</button>
        </div>
      </div>
    </div>
  </div>

  <script>
    const toggle = document.getElementById('billing-toggle');
    const monthlyLabel = document.getElementById('monthly-label');
    const annualLabel = document.getElementById('annual-label');
    const amounts = document.querySelectorAll('.amount');
    const notes = document.querySelectorAll('.billing-note');

    toggle.addEventListener('change', () => {
      const isAnnual = toggle.checked;

      if (isAnnual) {
        monthlyLabel.classList.remove('active');
        annualLabel.classList.add('active');
      } else {
        annualLabel.classList.remove('active');
        monthlyLabel.classList.add('active');
      }

      amounts.forEach(amount => {
        const val = isAnnual ? amount.getAttribute('data-annual') : amount.getAttribute('data-monthly');
        amount.textContent = val;
      });

      notes.forEach(note => {
        note.textContent = isAnnual ? 'Billed annually' : 'Billed monthly';
      });
    });

    function selectCard(planId) {
      document.querySelectorAll('.card').forEach(card => card.classList.remove('selected'));
      document.querySelectorAll('.btn').forEach(btn => {
        btn.classList.remove('selected-btn');
        if (btn.closest('#card-pro')) {
          btn.textContent = 'Select Pro';
        } else if (btn.closest('#card-starter')) {
          btn.textContent = 'Select Starter';
        } else if (btn.closest('#card-enterprise')) {
          btn.textContent = 'Select Enterprise';
        }
      });

      const selectedCard = document.getElementById(`card-${planId}`);
      selectedCard.classList.add('selected');

      const targetBtn = selectedCard.querySelector('.btn');
      targetBtn.classList.add('selected-btn');
      targetBtn.textContent = 'Plan Selected ✓';
    }

    function handleSelect(planId, event) {
      event.stopPropagation();
      selectCard(planId);
    }
  </script>
</body>
</html>
