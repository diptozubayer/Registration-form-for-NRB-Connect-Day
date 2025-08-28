Here’s a clean, ready-to-use HTML registration form that captures your requested fields. It includes dropdowns for **Industry** and **Occupation**, plus **Country/State (Region)**, **Address**, and **Sector**—with basic validation and smart “Other / Self-describe” reveal fields. Copy-paste into a file like `registration.html` and open in any browser.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>Registration Form</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root { --maxw: 840px; }
    * { box-sizing: border-box; }
    body { font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif; margin: 0; background: #f7f7fb; color: #222; }
    .wrap { max-width: var(--maxw); margin: 40px auto; padding: 0 16px; }
    h1 { font-size: 1.6rem; margin: 0 0 16px; }
    p.lead { margin: 0 0 24px; color: #555; }
    form { background: #fff; border: 1px solid #e8e8ef; border-radius: 12px; padding: 20px; }
    fieldset { border: 0; padding: 0; margin: 0 0 18px; }
    legend { font-weight: 700; margin-bottom: 12px; }
    .grid { display: grid; gap: 14px; }
    @media (min-width: 720px) {
      .grid.cols-2 { grid-template-columns: 1fr 1fr; }
      .grid.cols-3 { grid-template-columns: 1fr 1fr 1fr; }
    }
    label { display: block; font-size: 0.92rem; margin: 0 0 6px; color: #333; }
    input[type="text"], input[type="date"], select, textarea {
      width: 100%; padding: 10px 12px; border: 1px solid #dcdce5; border-radius: 10px; background: #fff; font: inherit;
    }
    textarea { min-height: 88px; resize: vertical; }
    .hint { font-size: 0.85rem; color: #777; margin-top: 6px; }
    .row { display: flex; gap: 12px; align-items: center; flex-wrap: wrap; }
    .row > label.inline { margin: 0 10px 0 0; }
    .hidden { display: none; }
    .actions { display: flex; gap: 10px; margin-top: 8px; flex-wrap: wrap; }
    button {
      appearance: none; border: 0; padding: 12px 16px; border-radius: 10px; cursor: pointer; font-weight: 600;
    }
    button[type="submit"] { background: #1f6feb; color: #fff; }
    button[type="reset"] { background: #eef2ff; color: #1f2a5a; }
    .summary { margin-top: 18px; background: #fbfcff; border: 1px solid #e8ecff; border-radius: 10px; padding: 12px; }
    .req::after { content: " *"; color: #c00; }
  </style>
</head>
<body>
  <div class="wrap">
    <h1>Registration Form</h1>
    <p class="lead">Please complete all required fields (marked with *).</p>

    <form id="regForm" novalidate>
      <!-- Personal Information -->
      <fieldset>
        <legend>Personal Information</legend>
        <div class="grid cols-2">
          <div>
            <label for="fullName" class="req">Full Name</label>
            <input id="fullName" name="fullName" type="text" autocomplete="name" required />
          </div>
          <div>
            <label for="dob" class="req">Date of Birth</label>
            <input id="dob" name="dob" type="date" required min="1900-01-01" />
          </div>
        </div>

        <div class="row" style="margin-top:10px;">
          <label class="inline req">Gender</label>
          <label><input type="radio" name="gender" value="Male" required /> Male</label>
          <label><input type="radio" name="gender" value="Female" /> Female</label>
          <label><input type="radio" name="gender" value="Non-binary" /> Non-binary</label>
          <label><input type="radio" name="gender" value="Prefer not to say" /> Prefer not to say</label>
          <label><input type="radio" name="gender" value="Self-describe" id="genderOtherRadio" /> Self-describe</label>
          <input type="text" id="genderOtherText" class="hidden" placeholder="Describe your gender" />
        </div>
      </fieldset>

      <!-- Professional Information -->
      <fieldset>
        <legend>Professional Information</legend>
        <div class="grid cols-2">
          <div>
            <label for="industry" class="req">Industry</label>
            <select id="industry" name="industry" required>
              <option value="" disabled selected>Select your industry</option>
              <option>Agriculture & Agribusiness</option>
              <option>Manufacturing</option>
              <option>Construction & Infrastructure</option>
              <option>Transportation & Logistics</option>
              <option>ICT / Software / ITES</option>
              <option>Telecom</option>
              <option>Finance & Banking</option>
              <option>Insurance</option>
              <option>Healthcare & Pharmaceuticals</option>
              <option>Education</option>
              <option>Retail & E-commerce</option>
              <option>Energy & Utilities</option>
              <option>Hospitality & Tourism</option>
              <option>Government & Public Administration</option>
              <option>Non-profit / NGO</option>
              <option>Media & Creative</option>
              <option>Real Estate</option>
              <option>Legal & Consulting</option>
              <option>Mining & Natural Resources</option>
              <option>Other</option>
            </select>
            <input type="text" id="industryOther" class="hidden" placeholder="Please specify your industry" />
          </div>

          <div>
            <label for="occupation" class="req">Occupation (Role)</label>
            <select id="occupation" name="occupation" required>
              <option value="" disabled selected>Select your occupation</option>
              <option>Owner / Founder</option>
              <option>Chief Executive (CEO/MD)</option>
              <option>Executive / Senior Manager</option>
              <option>Manager</option>
              <option>Supervisor / Team Lead</option>
              <option>Engineer</option>
              <option>Technician</option>
              <option>Operator</option>
              <option>IT / Software Developer</option>
              <option>Data Analyst / Scientist</option>
              <option>Researcher / Scientist</option>
              <option>Healthcare Professional</option>
              <option>Teacher / Faculty</option>
              <option>Sales / Marketing</option>
              <option>Finance / Accounting</option>
              <option>HR / People Ops</option>
              <option>Legal / Compliance</option>
              <option>Designer / Creative</option>
              <option>Customer Support</option>
              <option>Public Servant</option>
              <option>Freelancer / Consultant</option>
              <option>Student</option>
              <option>Retired</option>
              <option>Unemployed</option>
              <option>Other</option>
            </select>
            <input type="text" id="occupationOther" class="hidden" placeholder="Please specify your occupation" />
          </div>
        </div>
      </fieldset>

      <!-- Geographical Information -->
      <fieldset>
        <legend>Geographical Information</legend>
        <div class="grid cols-3">
          <div>
            <label for="country" class="req">Country</label>
            <select id="country" name="country" required>
              <option value="" disabled selected>Select country</option>
              <option>Bangladesh</option>
              <option>India</option>
              <option>Pakistan</option>
              <option>Nepal</option>
              <option>Sri Lanka</option>
              <option>Bhutan</option>
              <option>Maldives</option>
              <option>Malaysia</option>
              <option>Singapore</option>
              <option>China</option>
              <option>Japan</option>
              <option>South Korea</option>
              <option>United States</option>
              <option>Canada</option>
              <option>United Kingdom</option>
              <option>Germany</option>
              <option>France</option>
              <option>United Arab Emirates</option>
              <option>Saudi Arabia</option>
              <option>Qatar</option>
              <option>Oman</option>
              <option>Kuwait</option>
              <option>Australia</option>
              <option>New Zealand</option>
              <option>South Africa</option>
              <option>Nigeria</option>
              <option>Kenya</option>
              <option>Brazil</option>
              <option>Mexico</option>
              <option>Other</option>
            </select>
            <input type="text" id="countryOther" class="hidden" placeholder="Please specify your country" />
          </div>

          <div>
            <label for="state" class="req">State / Region / Province</label>
            <input id="state" name="state" type="text" required placeholder="e.g., Chattogram Division / Georgia / Maharashtra" />
          </div>

          <div>
            <label for="sector" class="req">Sector (Organization Type)</label>
            <select id="sector" name="sector" required>
              <option value="" disabled selected>Select sector</option>
              <option>Private Sector</option>
              <option>Public Sector (Govt/Agency)</option>
              <option>State-Owned Enterprise</option>
              <option>PPP / Concessionaire</option>
              <option>NGO / INGO</option>
              <option>Development Partner / Donor</option>
              <option>Academia / Research</option>
              <option>Startup / SME</option>
              <option>Other</option>
            </select>
            <input type="text" id="sectorOther" class="hidden" placeholder="Please specify your sector" />
          </div>
        </div>

        <div style="margin-top:14px;">
          <label for="address" class="req">Address</label>
          <textarea id="address" name="address" required placeholder="Street, area, postal code"></textarea>
          <div class="hint">Do not include highly sensitive information (e.g., apartment access codes).</div>
        </div>
      </fieldset>

      <!-- Consent -->
      <fieldset>
        <div class="row">
          <label>
            <input type="checkbox" id="consent" required />
            I confirm the information provided is accurate and I consent to its use for registration purposes.
          </label>
        </div>
      </fieldset>

      <div class="actions">
        <button type="submit">Submit</button>
        <button type="reset">Reset</button>
      </div>

      <div id="submitSummary" class="summary hidden" aria-live="polite"></div>
    </form>
  </div>

  <script>
    // Utility to toggle "Other / Self-describe" text inputs
    function toggleOnSelect(selectEl, triggerValue, targetInput) {
      const show = selectEl.value === triggerValue;
      targetInput.classList.toggle('hidden', !show);
      if (show) targetInput.focus();
      if (!show) targetInput.value = '';
    }

    // Gender self-describe
    const genderOtherRadio = document.getElementById('genderOtherRadio');
    const genderOtherText = document.getElementById('genderOtherText');
    document.querySelectorAll('input[name="gender"]').forEach(r => {
      r.addEventListener('change', () => {
        const show = genderOtherRadio.checked;
        genderOtherText.classList.toggle('hidden', !show);
        if (show) genderOtherText.focus(); else genderOtherText.value = '';
      });
    });

    // Industry / Occupation / Country / Sector "Other"
    const industry = document.getElementById('industry');
    const industryOther = document.getElementById('industryOther');
    industry.addEventListener('change', () => toggleOnSelect(industry, 'Other', industryOther));

    const occupation = document.getElementById('occupation');
    const occupationOther = document.getElementById('occupationOther');
    occupation.addEventListener('change', () => toggleOnSelect(occupation, 'Other', occupationOther));

    const country = document.getElementById('country');
    const countryOther = document.getElementById('countryOther');
    country.addEventListener('change', () => toggleOnSelect(country, 'Other', countryOther));

    const sector = document.getElementById('sector');
    const sectorOther = document.getElementById('sectorOther');
    sector.addEventListener('change', () => toggleOnSelect(sector, 'Other', sectorOther));

    // DOB max = today
    (function setDOBMax() {
      const today = new Date().toISOString().slice(0,10);
      document.getElementById('dob').setAttribute('max', today);
    })();

    // Handle submit with client-side validation + summary preview
    const form = document.getElementById('regForm');
    const summary = document.getElementById('submitSummary');
    form.addEventListener('submit', (e) => {
      e.preventDefault();

      // Native HTML5 validation
      if (!form.reportValidity()) return;

      // Build payload
      const data = {
        fullName: document.getElementById('fullName').value.trim(),
        dob: document.getElementById('dob').value,
        gender: (() => {
          const g = document.querySelector('input[name="gender"]:checked')?.value || '';
          return g === 'Self-describe' ? (document.getElementById('genderOtherText').value.trim() || 'Self-described') : g;
        })(),
        industry: industry.value === 'Other' ? (industryOther.value.trim() || 'Other') : industry.value,
        occupation: occupation.value === 'Other' ? (occupationOther.value.trim() || 'Other') : occupation.value,
        country: country.value === 'Other' ? (countryOther.value.trim() || 'Other') : country.value,
        stateRegion: document.getElementById('state').value.trim(),
        sector: sector.value === 'Other' ? (sectorOther.value.trim() || 'Other') : sector.value,
        address: document.getElementById('address').value.trim(),
        consent: document.getElementById('consent').checked
      };

      summary.classList.remove('hidden');
      summary.innerHTML = `
        <strong>Submission received.</strong>
        <div class="hint">Below is a preview of your data (for confirmation only).</div>
        <pre style="overflow:auto; white-space:pre-wrap; margin-top:8px;">${JSON.stringify(data, null, 2)}</pre>
      `;

      // TODO: Replace this with an actual POST to your backend
      console.log('Form payload:', data);
      alert('Thank you! Your registration has been submitted.');
      form.reset();
      // Hide conditionals after reset
      [industryOther, occupationOther, countryOther, sectorOther, genderOtherText].forEach(el => el.classList.add('hidden'));
    });

    // Reset handler
    form.addEventListener('reset', () => {
      setTimeout(() => {
        [industryOther, occupationOther, countryOther, sectorOther, genderOtherText].forEach(el => el.classList.add('hidden'));
        summary.classList.add('hidden');
        summary.innerHTML = '';
      }, 0);
    });
  </script>
</body>
</html>
```

If you’d like this exported as a **fillable Word/PDF** or turned into a **React component** with form validation libraries (e.g., React Hook Form + Zod), say the word and I’ll convert it for you.
