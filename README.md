# NeuroSync-V2
What if we could predict overwhelm before it happens? NeuroSync V2 explores how digital twins could help neurodivergent individuals identify patterns, anticipate challenges, and receive personalized support.
<div class="container">
  <h1>NeuroSync V2</h1>

  <div class="card">
    <h2>Current State Analysis</h2>

    <label>Heart Rate</label>
    <input id="heartRate" type="number" value="80">

    <label>HRV</label>
    <select id="hrv">
      <option>High</option>
      <option>Low</option>
    </select>

    <label>Movement</label>
    <select id="movement">
      <option>Still</option>
      <option>Agitated</option>
    </select>

    <label>Noise Level</label>
    <select id="noise">
      <option>Quiet</option>
      <option>Loud</option>
    </select>

    <button onclick="calculateDistress()">
      Analyze
    </button>

    <h3 id="score">Distress Score: --</h3>
    <h3 id="status">Status: --</h3>
    <p id="recommendation"></p>
  </div>

  <div class="card">
    <h2>Sensory Profile</h2>

    <select id="profile">
      <option>Seeker</option>
      <option>Avoider</option>
      <option>Mixed</option>
    </select>
  </div>

  <div class="card">
    <h2>Scenario Simulator</h2>

    <select id="scenario">
      <option>Quiet Bedroom</option>
      <option>Classroom</option>
      <option>Crowded Cafeteria</option>
      <option>Shopping Mall</option>
      <option>Sporting Event</option>
      <option>Family Gathering</option>
    </select>

    <button onclick="runScenario()">
      Predict
    </button>

    <p id="prediction"></p>
  </div>

  <div class="card">
    <h2>Trigger Mapping</h2>

    <label><input type="checkbox"> Noise</label>
    <label><input type="checkbox"> Crowds</label>
    <label><input type="checkbox"> Bright Lights</label>
    <label><input type="checkbox"> Sudden Changes</label>
    <label><input type="checkbox"> Social Pressure</label>
  </div>

  <div class="card">
    <h2>Daily Reflection</h2>

    <input
      id="mood"
      placeholder="Mood Today"
    >

    <textarea
      id="notes"
      placeholder="How are you feeling?"
    ></textarea>

    <button onclick="saveJournal()">
      Save Reflection
    </button>

    <div id="journalEntries"></div>
  </div>

  <div class="card">
    <h2>Intervention Feedback</h2>

    <button onclick="rateIntervention('Very Helpful')">
      Very Helpful
    </button>

    <button onclick="rateIntervention('Somewhat Helpful')">
      Somewhat Helpful
    </button>

    <button onclick="rateIntervention('Not Helpful')">
      Not Helpful
    </button>

    <p id="feedbackResult"></p>
  </div>

</div>
