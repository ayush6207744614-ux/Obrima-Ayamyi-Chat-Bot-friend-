
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>OBRIMA - AYAMIN AI</title>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, sans-serif;
  background: #090d1c;
  color: white;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 7%;
  background: #11182b;
  flex-wrap: wrap;
  gap: 15px;
}

.logo {
  font-size: 28px;
  font-weight: bold;
  color: #a78bfa;
}

select {
  padding: 10px;
  border-radius: 8px;
  background: #202b45;
  color: white;
  border: 1px solid #596580;
}

.hero {
  text-align: center;
  padding: 65px 20px;
}

.hero h1 {
  font-size: 48px;
  color: #b69aff;
  margin-bottom: 15px;
}

.hero p {
  color: #c4c9dc;
  font-size: 17px;
  margin-bottom: 25px;
}

button {
  border: none;
  padding: 13px 22px;
  border-radius: 10px;
  background: #8b5cf6;
  color: white;
  font-size: 15px;
  cursor: pointer;
}

button:hover {
  background: #7042d8;
}

.section {
  padding: 40px 7%;
  text-align: center;
}

.section h2 {
  font-size: 30px;
  margin-bottom: 25px;
}

.chatbox {
  max-width: 650px;
  margin: auto;
  background: #151e35;
  border: 1px solid #34415f;
  border-radius: 18px;
  padding: 20px;
}

.messages {
  height: 250px;
  overflow-y: auto;
  text-align: left;
  margin-bottom: 15px;
}

.message {
  background: #293553;
  padding: 12px;
  border-radius: 10px;
  margin-bottom: 12px;
  line-height: 1.5;
  overflow-wrap: anywhere;
}

.input-area {
  display: flex;
  gap: 8px;
}

.input-area input {
  flex: 1;
  min-width: 0;
  padding: 13px;
  border-radius: 9px;
  border: none;
  outline: none;
}

.pricing {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
  gap: 18px;
}

.plan {
  background: #151e35;
  padding: 25px;
  border: 1px solid #35415e;
  border-radius: 16px;
}

.plan h3 {
  color: #b69aff;
  margin-bottom: 15px;
}

.price {
  font-size: 30px;
  font-weight: bold;
  margin-bottom: 12px;
}

.plan p {
  color: #c4c9dc;
  margin: 10px 0 18px;
}

.plan button {
  width: 100%;
}

.note {
  color: #aeb8ce;
  font-size: 13px;
  margin-top: 20px;
  line-height: 1.6;
}

footer {
  text-align: center;
  padding: 25px;
  background: #11182b;
  color: #aeb8ce;
}
</style>
</head>

<body>

<header>
  <div class="logo">OBRIMA ✦</div>

  <select id="country">
    <option value="India">India 🇮🇳</option>
    <option value="Russia">Russia 🇷🇺</option>
    <option value="Norway">Norway 🇳🇴</option>
    <option value="North America">North America 🌎</option>
  </select>
</header>

<section class="hero">
  <h1>Meet AYAMIN</h1>
  <p>Your AI Friend. Your Ideas. Your World.</p>
  <button onclick="startChat()">Start Chatting</button>
  <p style="margin-top:18px">
    1 Minute Free Trial
  </p>
</section>

<section class="section" id="chatSection">
  <h2>AYAMIN AI Chat</h2>

  <div class="chatbox">
    <div class="messages" id="messages">
      <div class="message">
        <b>AYAMIN:</b> Hello! Welcome to OBRIMA.
        How can I help you today?
      </div>
    </div>

    <div class="input-area">
      <input
        id="userInput"
        type="text"
        placeholder="Message AYAMIN..."
        onkeydown="if(event.key==='Enter') sendMessage()"
      >
      <button onclick="sendMessage()">Send</button>
    </div>
  </div>
</section>

<section class="section">
  <h2>Choose Your Plan</h2>

  <div class="pricing">

    <div class="plan">
      <h3>Free Trial</h3>
      <div class="price">$0</div>
      <p>1 Minute Free Access</p>
      <button onclick="startChat()">Start Free</button>
    </div>

    <div class="plan">
      <h3>Hourly</h3>
      <div class="price">$0.10</div>
      <p>Access for 1 Hour</p>
      <button onclick="paymentNotice()">Choose Hourly</button>
    </div>

    <div class="plan">
      <h3>Weekly</h3>
      <div class="price">$1</div>
      <p>Access for 7 Days</p>
      <button onclick="paymentNotice()">Choose Weekly</button>
    </div>

    <div class="plan">
      <h3>Monthly</h3>
      <div class="price">Coming Soon</div>
      <p>30 Days Subscription</p>
      <button onclick="paymentNotice()">Choose Monthly</button>
    </div>

    <div class="plan">
      <h3>Yearly</h3>
      <div class="price">Coming Soon</div>
      <p>12 Months Subscription</p>
      <button onclick="paymentNotice()">Choose Yearly</button>
    </div>

  </div>

  <p class="note">
    Prices are displayed in USD. Monthly and yearly
    prices will be announced later.
    Payment services are not connected yet.
  </p>
</section>

<footer>
  <h3>OBRIMA ✦ AYAMIN</h3>
  <p>Your AI Friend, Everywhere.</p>
  <p>© 2026 OBRIMA. All rights reserved.</p>
</footer>

<script>
function startChat() {
  document.getElementById("chatSection")
    .scrollIntoView({behavior:"smooth"});
  document.getElementById("userInput").focus();
}

function sendMessage() {
  const input = document.getElementById("userInput");
  const messages = document.getElementById("messages");
  const text = input.value.trim();

  if (!text) return;

  const user = document.createElement("div");
  user.className = "message";
  user.textContent = "You: " + text;
  messages.appendChild(user);

  const reply = document.createElement("div");
  reply.className = "message";
  reply.textContent =
    "AYAMIN: Thanks for your message! I'm currently a demo chatbot. My AI brain is coming soon!";
  messages.appendChild(reply);

  input.value = "";
  messages.scrollTop = messages.scrollHeight;
}

function paymentNotice() {
  alert("OBRIMA payments are not connected yet. Please check back later.");
}
</script>

</body>
</html>
