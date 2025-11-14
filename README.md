# Destiny- <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Destiny Delivery Company Tracking</title>
<style>
body {
  margin: 0;
  font-family: 'Open Sans', sans-serif;
  background-color: #1A1A1A;
  color: #FFFFFF;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  background-color: #111111;
}
header h1 {
  color: #007BFF;
  font-family: 'Montserrat', sans-serif;
  font-size: 22px;
}
.tracking-section {
  text-align: center;
  padding: 30px;
}
.tracking-section input {
  padding: 10px;
  width: 60%;
  max-width: 300px;
  border-radius: 5px;
  border: none;
}
.tracking-section button {
  padding: 10px 20px;
  margin-left: 10px;
  background-color: #007BFF;
  color: #FFFFFF;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.tracking-section button:hover {
  background-color: #FF3B3F;
}
.timeline {
  margin: 40px auto;
  max-width: 500px;
}
.timeline-item {
  padding: 15px;
  border-left: 4px solid #007BFF;
  margin-bottom: 20px;
  position: relative;
}
.timeline-item.current {
  border-left-color: #FF3B3F;
}
.timeline-item::before {
  content: '';
  position: absolute;
  left: -8px;
  top: 10px;
  width: 12px;
  height: 12px;
  background-color: #007BFF;
  border-radius: 50%;
}
.timeline-item.current::before {
  background-color: #FF3B3F;
}
footer {
  text-align: center;
  padding: 20px;
  background-color: #111111;
  margin-top: 50px;
}

/* Responsive */
@media screen and (max-width: 600px) {
  .tracking-section input {
    width: 80%;
    margin-bottom: 10px;
  }
  .tracking-section button {
    width: 50%;
    margin-left: 0;
  }
}
</style>

<!-- Google Translate Widget -->
<script type="text/javascript">
function googleTranslateElementInit() {
  new google.translate.TranslateElement({pageLanguage: 'en', layout: google.translate.TranslateElement.InlineLayout.HORIZONTAL}, 'google_translate_element');
}
</script>
<script type="text/javascript" src="//translate.google.com/translate_a/element.js?cb=googleTranslateElementInit"></script>

</head>
<body>

<header>
  <h1>DESTINY DELIVERY COMPANY</h1>
  <div id="google_translate_element"></div>
</header>

<div class="tracking-section">
  <h2>Create or Track Your Package</h2>
  <button onclick="generateTrackingNumber()">Create Tracking Number</button><br><br>
  <input type="text" placeholder="Enter Tracking Number" id="trackingInput">
  <button onclick="trackPackageDemo()">Track Package</button>
</div>

<div class="timeline">
  <div class="timeline-item">Order Received</div>
  <div class="timeline-item">Picked Up</div>
  <div class="timeline-item">In Transit</div>
  <div class="timeline-item">Arrived at Sorting Center</div>
  <div class="timeline-item current">Out for Delivery</div>
  <div class="timeline-item">Delivered</div>
</div>

<footer>
  © 2025 Destiny Delivery Company | Contact: info@destinydelivery.com
</footer>

<script>
let currentTrackingNumber = '';

function generateTrackingNumber() {
  let serial = Math.floor(Math.random() * 1000000).toString().padStart(6,'0');
  currentTrackingNumber = `DDC-2025-${serial}`;
  alert('Your new tracking number is: ' + currentTrackingNumber);
  document.getElementById('trackingInput').value = currentTrackingNumber;
  resetTimeline();
}

// Demo tracking function
function trackPackageDemo() {
  let number = document.getElementById('trackingInput').value || currentTrackingNumber;
  if(!number){
    alert('Please enter or create a tracking number.');
    return;
  }
  
  const steps = document.querySelectorAll('.timeline-item');
  // Random current step for demo
  let progress = Math.floor(Math.random() * steps.length);
  steps.forEach((step, index) => {
    step.classList.remove('current');
    if(index === progress){
      step.classList.add('current');
    }
  });
  alert('Tracking info for: ' + number);
}

// Reset timeline to first step
function resetTimeline(){
  const steps = document.querySelectorAll('.timeline-item');
  steps.forEach(step => step.classList.remove('current'));
  steps[0].classList.add('current');
}

// Optional: Auto-move timeline for demo every 5 sec
setInterval(() => {
  const steps = document.querySelectorAll('.timeline-item');
  const currentIndex = [...steps].findIndex(s => s.classList.contains('current'));
  if(currentIndex < steps.length - 1){
    steps[currentIndex].classList.remove('current');
    steps[currentIndex+1].classList.add('current');
  }
}, 5000);

</script>

</body>
</html>
