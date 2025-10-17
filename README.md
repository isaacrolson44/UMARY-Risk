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
      background: linear-gradient(135deg, #f0f4ff 0%, #ffffff 100%);
      color: #222;
      line-height: 1.6;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }
    a {
      color: #FF6A00; /* University of Mary Orange */
      text-decoration: none;
      transition: color 0.3s ease;
    }
    a:hover,
    a:focus {
      color: #cc5600;
      text-decoration: underline;
      outline: none;
    }

    /* Header */
    header {
      background-color: #0033A0; /* University of Mary Blue */
      color: white;
      padding: 20px 40px;
      display: flex;
      align-items: center;
      gap: 20px;
      flex-wrap: wrap;
      box-shadow: 0 4px 8px rgba(0, 51, 160, 0.4);
      position: sticky;
      top: 0;
      z-index: 1000;
    }
    header img {
      height: 70px;
      width: auto;
      filter: drop-shadow(0 0 2px rgba(0,0,0,0.3));
      border-radius: 8px;
      transition: transform 0.3s ease;
    }
    header img:hover,
    header img:focus {
      transform: scale(1.05);
      outline: none;
    }
    header h1 {
      font-size: 2rem;
      margin: 0;
      flex: 1 1 auto;
      font-weight: 700;
      text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
    }

    /* Main container */
    main {
      max-width: 1100px;
      margin: 40px auto 80px;
      background: white;
      padding: 40px 50px;
      border-radius: 12px;
      box-shadow: 0 8px 24px rgba(0, 51, 160, 0.15);
      flex-grow: 1;
    }

    /* Section headings */
    h2 {
      color: #0033A0;
      border-bottom: 4px solid #FF6A00;
      padding-bottom: 10px;
      margin-bottom: 30px;
      font-weight: 800;
      font-size: 2rem;
      letter-spacing: 1px;
    }
    h3 {
      font-weight: 700;
      font-size: 1.3rem;
      margin: 0;
      display: flex;
      align-items: center;
      gap: 12px;
      color: #003366;
    }

    /* Areas of Risk Management container */
    #areas-risk-management {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 30px;
      margin-bottom: 50px;
    }

    /* Individual risk area card */
    .risk-card {
      background-color: #f7fbff;
      border: 3px solid #0033A0;
      border-radius: 16px;
      padding: 25px 30px;
      box-shadow: 0 6px 16px rgba(0, 51, 160, 0.2);
      cursor: pointer;
      transition: box-shadow 0.4s ease, border-color 0.4s ease, transform 0.3s ease;
      display: flex;
      flex-direction: column;
      height: 100%;
      position: relative;
      overflow: hidden;
    }
    .risk-card:hover,
    .risk-card:focus {
      box-shadow: 0 12px 28px rgba(255, 106, 0, 0.5);
      border-color: #FF6A00;
      transform: translateY(-6px);
      outline: none;
      z-index: 10;
    }

    /* Icon style */
    .risk-icon {
      font-size: 2.2rem;
      color: #FF6A00;
      flex-shrink: 0;
    }

    /* Content inside card, initially hidden */
    .risk-content {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.5s ease, opacity 0.5s ease;
      color: #002366;
      font-size: 1.05rem;
      margin-top: 15px;
      flex-grow: 1;
      opacity: 0;
    }

    /* Show content when active */
    .risk-card.active .risk-content {
      max-height: 600px; /* enough to show content */
      opacity: 1;
    }

    /* List inside content */
    .risk-content ul {
      padding-left: 22px;
      margin: 0;
      list-style-type: disc;
    }
    .risk-content li {
      margin-bottom: 10px;
      line-height: 1.5;
    }
    .risk-content strong {
      color: #001f4d;
    }

    /* Resources buttons */
    .resources {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      margin-top: 15px;
    }
    .resources a {
      background-color: #FF6A00;
      color: white;
      padding: 14px 28px;
      border-radius: 8px;
      font-weight: 700;
      box-shadow: 0 4px 10px rgba(255, 106, 0, 0.5);
      transition: background-color 0.3s ease, box-shadow 0.3s ease;
      flex: 1 1 220px;
      text-align: center;
      font-size: 1.1rem;
      user-select: none;
    }
    .resources a:hover,
    .resources a:focus {
      background-color: #cc5600;
      box-shadow: 0 6px 16px rgba(204, 86, 0, 0.7);
      outline: none;
    }

    /* Contact info */
    .contact-info p {
      margin: 8px 0;
      font-size: 1.1rem;
      color: #003366;
    }
    .contact-info a {
      font-weight: 700;
      color: #FF6A00;
      transition: color 0.3s ease;
    }
    .contact-info a:hover,
    .contact-info a:focus {
      color: #cc5600;
      outline: none;
    }

    /* News & updates */
    .news-updates {
      background-color: #e6f0ff;
      padding: 25px 30px;
      border-radius: 12px;
      font-size: 1.1rem;
      color: #0033A0;
      box-shadow: inset 0 0 12px rgba(0, 51, 160, 0.2);
      font-style: italic;
      user-select: none;
    }

    /* Incident form */
    form label {
      font-weight: 700;
      font-size: 1.05rem;
      display: block;
      margin-bottom: 6px;
      color: #003366;
    }
    form input[type="text"],
    form input[type="email"],
    form textarea {
      width: 100%;
      padding: 10px 14px;
      margin-bottom: 20px;
      border: 2px solid #ccc;
      border-radius: 8px;
      font-size: 1rem;
      font-family: inherit;
      resize: vertical;
      transition: border-color 0.3s ease;
    }
    form input[type="text"]:focus,
    form input[type="email"]:focus,
    form textarea:focus {
      border-color: #FF6A00;
      outline: none;
      box-shadow: 0 0 8px rgba(255, 106, 0, 0.6);
    }
    form button[type="submit"] {
      background-color: #FF6A00;
      color: white;
      border: none;
      padding: 14px 30px;
      font-size: 1.2rem;
      border-radius: 10px;
      cursor: pointer;
      font-weight: 800;
      transition: background-color 0.3s ease, box-shadow 0.3s ease;
      user-select: none;
      box-shadow: 0 6px 14px rgba(255, 106, 0, 0.6);
    }
    form button[type="submit"]:hover,
    form button[type="submit"]:focus {
      background-color: #cc5600;
      box-shadow: 0 8px 20px rgba(204, 86, 0, 0.8);
      outline: none;
    }

    /* Responsive */
    @media (max-width: 700px) {
      main {
        padding: 30px 25px;
        margin: 20px 15px 80px;
      }
      header {
        justify-content: center;
        text-align: center;
      }
      header h1 {
        font-size: 1.6rem;
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
      padding: 18px 20px;
      font-size: 1rem;
      user-select: none;
      box-shadow: 0 -3px 12px rgba(0, 0, 0, 0.25);
    }
  </style>
</head>
<body>
  <header>
    <img src="https://www.umary.edu/_resources/images/umary-logo.svg" alt="University of Mary Logo" tabindex="0" />
    <img src="https://i.imgur.com/0Xq6Xqv.png" alt="University of Mary Marauders Logo" tabindex="0" style="height:70px; width:auto;" />
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
      <div id="areas-risk-management" role="list">
        <div class="risk-card" tabindex="0" aria-expanded="false" role="button" aria-controls="property-content" aria-label="Property and Casualty Insurance details">
          <h3><span class="risk-icon" aria-hidden="true">🏢</span> Property &amp; Casualty Insurance</h3>
          <div class="risk-content" id="property-content" role="region" aria-live="polite">
            <ul>
              <li><strong>Campus Property Insurance</strong><br />Protecting University of Mary’s physical assets including buildings, equipment, and vehicles.</li>
              <li><strong>Liability Insurance</strong><br />Coverage for general liability, professional liability, and special events.</li>
              <li><strong>Vehicle Insurance</strong><br />Policies for university-owned vehicles and driver safety programs.</li>
            </ul>
          </div>
        </div>

        <div class="risk-card" tabindex="0" aria-expanded="false" role="button" aria-controls="health-content" aria-label="Health and Safety details">
          <h3><span class="risk-icon" aria-hidden="true">🩺</span> Health &amp; Safety</h3>
          <div class="risk-content" id="health-content" role="region" aria-live="polite">
            <ul>
              <li><strong>Workplace Safety Programs</strong><br />Training and resources to prevent workplace injuries and illnesses.</li>
              <li><strong>Environmental Health &amp; Safety</strong><br />Compliance with environmental regulations and hazardous materials management.</li>
              <li><strong>Emergency Preparedness</strong><br />Planning and response for natural disasters, fire, and other emergencies.</li>
            </ul>
          </div>
        </div>

        <div class="risk-card" tabindex="0" aria-expanded="false" role="button" aria-controls="compliance-content" aria-label="Compliance and Legal Risk details">
          <h3><span class="risk-icon" aria-hidden="true">⚖️</span> Compliance &amp; Legal Risk</h3>
          <div class="risk-content" id="compliance-content" role="region" aria-live="polite">
            <ul>
              <li><strong>Regulatory Compliance</strong><br />Ensuring adherence to federal, state, and local laws affecting campus operations.</li>
              <li><strong>Contract Review</strong><br />Risk assessment and review of contracts and agreements.</li>
              <li><strong>Privacy &amp; Data Security</strong><br />Protecting sensitive information and maintaining data privacy standards.</li>
            </ul>
          </div>
        </div>

        <div class="risk-card" tabindex="0" aria-expanded="false" role="button" aria-controls="student-content" aria-label="Student and Campus Risk details">
          <h3><span class="risk-icon" aria-hidden="true">🎓</span> Student &amp; Campus Risk</h3>
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
        <label for="name">Name<span aria-hidden="true">*</span>:</label>
        <input type="text" id="name" name="name" required aria-required="true" />

        <label for="email">Email<span aria-hidden="true">*</span>:</label>
        <input type="email" id="email" name="email" required aria-required="true" />

        <label for="details">Incident Details<span aria-hidden="true">*</span>:</label>
        <textarea id="details" name="details" rows="5" required aria-required="true"></textarea>

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

