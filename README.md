<html lang="en">
}
button {
background: navy;
color: white;
border: none;
cursor: pointer;
}
button:hover {
background: #000066;
}
</style>
</head>
<body>
<div class="container">
<div class="left-panel">
<input id="userId" type="text" placeholder="user 18 digit id">
<input id="nickname" type="text" placeholder="nickname">
<input id="prize" type="text" placeholder="prize name">
<input id="duration" type="text" placeholder="duration (e.g. 2d)">
<input id="winners" type="number" placeholder="# of winners" min="1" max="5" value="1">
<button id="submitBtn">Submit</button>
</div>
<div class="right-panel">
<textarea id="paragraph" readonly>paragraph will appear here</textarea>
<textarea id="code" readonly>giveaway code will appear here</textarea>
</div>
</div>


<script>
function generateGiveaway() {
const userId = document.getElementById('userId').value.trim();
const nickname = document.getElementById('nickname').value.trim();
const prize = document.getElementById('prize').value.trim();
const duration = document.getElementById('duration').value.trim();
let winners = parseInt(document.getElementById('winners').value.trim(), 10);


if (!userId || !nickname || !prize || !duration || !winners) {
alert("Please fill in all fields.");
return;
}


if (winners > 5) {
winners = 5;
alert("The number of winners cannot exceed 5. It has been capped at 5.");
}


const paragraph = `Thank you, <@${userId}>, for giving away ${prize}! If you are drawn as a winner, you have 24 hours to message ${nickname} to claim your prize. Do not message them unless you are the winner. Thank you, ${nickname}, once again for the generosity! Good luck to all who enter!`;


const code = `/start ${duration} ${prize} ${winners}`;


document.getElementById('paragraph').value = paragraph;
document.getElementById('code').value = code;
}


document.getElementById('submitBtn').addEventListener('click', generateGiveaway);
</script>
</body>
</html>
