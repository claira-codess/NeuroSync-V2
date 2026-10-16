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
body{
  font-family: Arial, sans-serif;
  background:#f4f6f9;
  padding:20px;
}

.container{
  max-width:1000px;
  margin:auto;
}

h1{
  text-align:center;
  color:#1f3c88;
}

.card{
  background:white;
  padding:20px;
  margin:20px 0;
  border-radius:12px;
  box-shadow:0 2px 8px rgba(0,0,0,0.1);
}

button{
  background:#1f3c88;
  color:white;
  border:none;
  padding:10px 15px;
  border-radius:6px;
  cursor:pointer;
}

button:hover{
  background:#3458b3;
}

input,
textarea,
select{
  width:100%;
  margin:8px 0;
  padding:8px;
}

.stable{
  color:green;
}

.elevated{
  color:orange;
}

.high{
  color:red;
}
let currentScore = 0;

function calculateDistress(){

  const heartRate =
    Number(document.getElementById("heartRate").value);

  const hrv =
    document.getElementById("hrv").value;

  const movement =
    document.getElementById("movement").value;

  const noise =
    document.getElementById("noise").value;

  let score = 0;

  score += heartRate > 100 ? 30 : 10;
  score += hrv === "Low" ? 25 : 5;
  score += movement === "Agitated" ? 20 : 0;
  score += noise === "Loud" ? 25 : 5;

  currentScore = score;

  let status = "";
  let recommendation = "";

  if(score >= 70){
    status = "High Risk";
  }
  else if(score >= 40){
    status = "Elevated";
  }
  else{
    status = "Stable";
  }

  const profile =
    document.getElementById("profile").value;

  if(profile === "Seeker"){
    recommendation =
      "Try movement, music, or tactile stimulation.";
  }

  if(profile === "Avoider"){
    recommendation =
      "Move to a quieter environment and reduce sensory input.";
  }

  if(profile === "Mixed"){
    recommendation =
      "Balance calming strategies with controlled stimulation.";
  }

  document.getElementById("score").innerText =
    "Distress Score: " + score;

  document.getElementById("status").innerText =
    "Status: " + status;

  document.getElementById("recommendation").innerText =
    recommendation;
}

function runScenario(){

  const scenario =
    document.getElementById("scenario").value;

  const scenarios = {
    "Quiet Bedroom":5,
    "Classroom":20,
    "Crowded Cafeteria":40,
    "Shopping Mall":50,
    "Sporting Event":35,
    "Family Gathering":25
  };

  const predicted =
    currentScore + scenarios[scenario];

  document.getElementById("prediction").innerText =
    "Predicted Distress Score: " + predicted;
}

function saveJournal(){

  const mood =
    document.getElementById("mood").value;

  const notes =
    document.getElementById("notes").value;

  const entry =
    `<p><strong>${mood}</strong><br>${notes}</p>`;

  let existing =
    localStorage.getItem("journal") || "";

  existing += entry;

  localStorage.setItem(
    "journal",
    existing
  );

  loadJournal();
}

function loadJournal(){

  document.getElementById(
    "journalEntries"
  ).innerHTML =
    localStorage.getItem("journal") || "";
}

function rateIntervention(rating){

  document.getElementById(
    "feedbackResult"
  ).innerText =
    "Last intervention rated: " + rating;
}

loadJournal();
