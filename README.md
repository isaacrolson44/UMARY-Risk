# UMARY-Risk
University of Mary Risk Management Portal
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>University of Mary Risk Management</title>
  <link href="https://fonts.googleapis.com/css2?family=Open+Sans&display=swap" rel="stylesheet" />
  <style>
    /* Reset and base */
    * {
      box-sizing: border-box;
    }
    body {
      font-family: 'Open Sans', Arial, sans-serif;
      margin: 0;
      background-color: #f5f7fa;
      color: #333;
      line-height: 1.6;
    }
    a {
      color: #FF6A00; /* University of Mary Orange */
      text-decoration: none;
    }
    a:hover,
    a:focus {
      text-decoration: underline;
    }

    /* Header */
    header {
      background-color: #0033A0; /* University of Mary Blue */
      color: white;
      padding: 20px 30px;
      display: flex;
      align-items: center;
      gap: 15px;
      flex-wrap: wrap;
    }
    header img {
      height: 50px;
      width: auto;
      margin-right: 10px;
    }
    header h1 {
      font-size: 1.8rem;
      margin: 0;
      flex: 1 1 auto;
    }

    /* Main container */
    main {
      max-width: 960px;
      margin: 30px auto 60px;
      background: white;
      padding: 30px 40px;
      border-radius: 8px;
      box-shadow: 0 4px 12px rgb(0 0 0 / 0.1);
    }

    /* Section headings */
    h2 {
      color: #0033A0;
      border-bottom: 3px solid #0033A0;
      padding-bottom: 8px;
      margin-bottom: 20px;
      font-weight: 700;
      font-size: 1.6rem;
    }
    h3 {
      font-weight: 600;
      font-size: 1.2rem;
      margin: 0;
    }

    /* Areas of Risk Management container */
    #areas-risk-management {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 25px;
      margin-bottom: 40px;
    }

    /* Individual risk area card */
    .risk-card {
      background-color: #f7fbff;
      border: 2px solid #0033A0;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 4px 8px rgb(0 51 160 / 0.15);
      cursor: pointer;
      transition: box-shadow 0.3s ease, border-color 0.3s ease;
      display: flex;
      flex-direction: column;
      height: 100%;
    }

    .risk-card:hover,
    .risk-card:focus {
      box-shadow: 0 8px 16px rgb(0 51 160 / 0.3);
      border-color: #FF6A00;
      outline: none;
    }

    .risk-card h3 {
      margin-top: 0;
      margin-bottom: 10px;
      color: #0033A0;
      font-size: 1.3rem;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    /* Icon style */
    .risk-icon {
      font-size: 1.8rem;
      color: #FF6A00;
    }

    /* Content inside card, initially hidden */
    .risk-content {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.4s ease;
      color: #002366;
      font-size: 1rem;
      margin-top: 10px;
      flex-grow: 1;
    }

    /* Show content when active */
    .risk-card.active .risk-content {
      max-height: 500px; /* enough to show content */
    }

    /* List inside content */
    .risk-content ul {
      padding-left: 20px;
      margin: 0;
    }

    .risk-content li {
      margin-bottom: 8px;
    }

    /* Resources buttons */
    .resources {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      margin-top: 10px;
    }
    .resources a {
      background-color: #FF6A00;
      color: white;
      padding: 12px 20px;
      border-radius: 6px;
      font-weight: 600;
      box-shadow: 0 2px 6px rgb(255 106 0 / 0.4);
      transition: background-color 0.3s ease;
      flex: 1 1 180px;
      text-align: center;
    }
    .resources a:hover,
    .resources a:focus {
      background-color: #cc5600;
    }

    /* Contact info */
    .contact-info p {
      margin: 6px 0;
      font-size: 1rem;
    }
    .contact-info a {
      font-weight: 600;
      color: #FF6A00;
    }

    /* News & updates */
    .news-updates {
      background-color: #e6f0ff;
      padding: 20px;
      border-radius: 8px;
      font-size: 1rem;
      color: #0033A0;
      box-shadow: inset 0 0 8px rgb(0 51 160 / 0.15);
    }

    /* Incident form */
    form label {
      font-weight: 600;
    }
    form input[type="text"],
    form input[type="email"],
    form textarea {
      width: 100%;
      padding: 8px 10px;
      margin-top: 4px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 1rem;
      font-family: inherit;
      resize: vertical;
    }
    form button[type="submit"] {
      background-color: #FF6A00;
      color: white;
      border: none;
      padding: 12px 25px;
      font-size: 1.1rem;
      border-radius: 6px;
      cursor: pointer;
      font-weight: 700;
      transition: background-color 0.3s ease;
    }
    form button[type="submit"]:hover,
    form button[type="submit"]:focus {
      background-color: #cc5600;
    }

    /* Responsive */
    @media (max-width: 600px) {
      main {
        padding: 20px 20px 40px;
        margin: 20px 10px 60px;
      }
      header {
        justify-content: center;
        text-align: center;
      }
      header h1 {
        font-size: 1.4rem;
      }
      .resources a {
        flex: 1 1 100%;
      }
    }

    /* Footer */
    footer {
      background-color: #0033A0;
      color: white;
      text-align: center;
      padding: 15px 20px;
      font-size: 0.9rem;
      position: fixed;
      bottom: 0;
      width: 100%;
      box-shadow: 0 -2px 8px rgb(0 0 0 / 0.15);
      user-select: none;
      z-index: 100;
    }
  </style>
</head>
<body>
  <header>
    <img src="https://www.umary.edu/_resources/images/umary-logo.svg" alt="University of Mary Logo" style="height:50px; width:auto; margin-right:10px;" />
    <img src="https://i.imgur.com/0Xq6Xqv.png" alt="University of Mary Marauders Logo" style="height:60px; width:auto; margin-right:10px;" />
    <h1>University of Mary Risk Management</h1>
  </header>

  <main>
    <section>
      <p>Welcome to the University of Mary Risk Management Office. Our mission is to support the University community by identifying, assessing, and mitigating risks to ensure a safe and secure environment for students, faculty, staff, and visitors.</p>
    </section>

    <section>
      <h2>About Us</h2>
      <p>The Risk Management Office at the University of Mary is dedicated to promoting a culture of safety and responsibility. We collaborate with campus departments to manage risks related to property, operations, personnel, and compliance.</p>
    </section>

    <section>
      <h2>Areas of Risk Management</h2>
      <div id="areas-risk-management">
        <div class="risk-card" tabindex="0" aria-expanded="false" role="button" aria-controls="property-content">
          <h3><span class="risk-icon">🏢</span> Property &amp; Casualty Insurance</h3>
          <div class="risk-content" id="property-content" role="region" aria-live="polite">
            <ul>
              <li><strong>Campus Property Insurance</strong><br />Protecting University of Mary’s physical assets including buildings, equipment, and vehicles.</li>
              <li><strong>Liability Insurance</strong><br />Coverage for general liability, professional liability, and special events.</li>
              <li><strong>Vehicle Insurance</strong><br />Policies for university-owned vehicles and driver safety programs.</li>
            </ul>
          </div>
        </div>

        <div class="risk-card" tabindex="0" aria-expanded="false" role="button" aria-controls="health-content">
          <h3><span class="risk-icon">🩺</span> Health &amp; Safety</h3>
          <div class="risk-content" id="health-content" role="region" aria-live="polite">
            <ul>
              <li><strong>Workplace Safety Programs</strong><br />Training and resources to prevent workplace injuries and illnesses.</li>
              <li><strong>Environmental Health &amp; Safety</strong><br />Compliance with environmental regulations and hazardous materials management.</li>
              <li><strong>Emergency Preparedness</strong><br />Planning and response for natural disasters, fire, and other emergencies.</li>
            </ul>
          </div>
        </div>

        <div class="risk-card" tabindex="0" aria-expanded="false" role="button" aria-controls="compliance-content">
          <h3><span class="risk-icon">⚖️</span> Compliance &amp; Legal Risk</h3>
          <div class="risk-content" id="compliance-content" role="region" aria-live="polite">
            <ul>
              <li><strong>Regulatory Compliance</strong><br />Ensuring adherence to federal, state, and local laws affecting campus operations.</li>
              <li><strong>Contract Review</strong><br />Risk assessment and review of contracts and agreements.</li>
              <li><strong>Privacy &amp; Data Security</strong><br />Protecting sensitive information and maintaining data privacy standards.</li>
            </ul>
          </div>
        </div>

        <div class="risk-card" tabindex="0" aria-expanded="false" role="button" aria-controls="student-content">
          <h3><span class="risk-icon">🎓</span> Student &amp; Campus Risk</h3>
          <div class="risk-content" id="student-content" role="region" aria-live="polite">
            <ul>
              <li><strong>Student Conduct &amp; Risk</strong><br />Programs to promote responsible behavior and reduce student-related risks.</li>
              <li><strong>Event Risk Management</strong><br />Guidelines and support for safe planning and execution of campus events.</li>
              <li><strong>Travel Risk Management</strong><br />Policies and resources for domestic and international travel by students and staff.</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <section>
      <h2>Resources</h2>
      <div class="resources">
        <a href="#" aria-label="Download Risk Management Policies">Risk Management Policies</a>
        <a href="#" aria-label="Report a Risk or Incident">Incident Reporting</a>
        <a href="#" aria-label="View Training and Workshops">Training &amp; Workshops</a>
        <a href="#" aria-label="Access Forms and Documents">Forms &amp; Documents</a>
      </div>
    </section>

    <section>
      <h2>Incident Reporting</h2>
      <form id="incidentForm" action="/api/report" method="POST" novalidate>
        <label for="name">Name<span aria-hidden="true">*</span>:</label><br />
        <input type="text" id="name" name="name" required /><br />

        <label for="email">Email<span aria-hidden="true">*</span>:</label><br />
        <input type="email" id="email" name="email" required /><br />

        <label for="details">Incident Details<span aria-hidden="true">*</span>:</label><br />
        <textarea id="details" name="details" rows="5" required></textarea><br />

        <button type="submit">Submit Report</button>
      </form>
      <p id="formMessage" role="alert" aria-live="assertive" style="color:green; display:none; margin-top:10px;"></p>
    </section>

    <section>
      <h2>Contact Us</h2>
      <div class="contact-info">
        <p><strong>Risk Management Office</strong></p>
        <p>University of Mary</p>
        <p>7500 University Drive, Bismarck, ND 58504</p>
        <p>Phone: <a href="tel:+17017773000">(701) 355-7300</a></p>
        <p>Email: <a href="mailto:riskmanagement@umary.edu">riskmanagement@umary.edu</a></p>
        <p><strong>Risk Manager:</strong> John Smith</p>
        <p>Phone: <a href="tel:+17013553123">(701) 355-3123</a></p>
        <p>Email: <a href="mailto:john.smith@umary.edu">john.smith@umary.edu</a></p>
      </div>
    </section>

    <section>
      <h2>News &amp; Updates</h2>
      <div class="news-updates" aria-live="polite" aria-atomic="true">
        <p>Stay informed about the latest risk management news, safety alerts, and campus initiatives.</p>
      </div>
    </section>
  </main>

  <footer>
    &copy; 2024 University of Mary Risk Management Office
  </footer>

  <script>
    // Toggle risk card content on click or keyboard (Enter/Space)
    document.querySelectorAll('.risk-card').forEach(card => {
      card.addEventListener('click', () => {
        toggleCard(card);
      });
      card.addEventListener('keydown', e => {
        if (e.key === 'Enter' || e.key === ' ') {
          e.preventDefault();
          toggleCard(card);
        }
      });
    });

    function toggleCard(card) {
      const isActive = card.classList.contains('active');
      // Close all cards
      document.querySelectorAll('.risk-card').forEach(c => {
        c.classList.remove('active');
        c.setAttribute('aria-expanded', 'false');
      });
      // Toggle current card
      if (!isActive) {
        card.classList.add('active');
        card.setAttribute('aria-expanded', 'true');
      }
    }

    // Incident form submission
    const form = document.getElementById('incidentForm');
    const message = document.getElementById('formMessage');

    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      message.style.display = 'none';
      const formData = {
        name: form.name.value.trim(),
        email: form.email.value.trim(),
        details: form.details.value.trim()
      };

      try {
        const response = await fetch('/api/report', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(formData)
        });
        if (response.ok) {
          message.textContent = 'Thank you! Your incident report has been submitted.';
          message.style.color = 'green';
          message.style.display = 'block';
          form.reset();
        } else {
          throw new Error('Submission failed');
        }
      } catch (error) {
        message.textContent = 'Sorry, there was an error submitting your report. Please try again later.';
        message.style.color = 'red';
        message.style.display = 'block';
      }
    });
  </script>
</body>
</html>
