<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Wolokoso Saving Group</title>
<link rel="stylesheet" href="style.css">

<!-- EmailJS -->
<script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
<script>
(function(){
emailjs.init("g8r7zKVFGoV7QBoJB"); // replace this
})();
</script>
</head>
<body>

<div class="container">
<h2>Wolokoso Saving Group</h2>

<p>P.O Box.....<br>Butaleja-Doho</p>
<p>wolokososavinggroup26@gmail.com</p>

<form id="savingForm">

<label>Date:</label>
<input type="date" name="date" required>

<label>Name:</label>
<input type="text" name="name" placeholder="Your name" required>

<label>Phone:</label>
<input type="text" name="phone" placeholder="Phone number" required>

<label>Amount:</label>
<input type="number" name="amount" placeholder="5000 - 1000000" required>

<label>Photo:</label>
<input type="file" id="photo" accept="image/*" required>
<img id="preview" style="display:none;" />

<button type="submit">Save Money</button>

</form>

<h3>Help Center</h3>

<div class="help-box">
<h4>Chairperson</h4>
<a href="tel:0788038536">📞Call</a>
<a href="https://wa.me/256788038536">WhatsApp</a>
<a href="sms:0788038536">SMS</a>
</div>

<div class="help-box">
<h4>Secretary</h4>
<a href="tel:0757640767">📞Call</a>
<a href="https://wa.me/256757640767">WhatsApp</a>
<a href="sms:0757640767">SMS</a>
</div>

<div class="help-box">
<h4>Treasurer</h4>
<a href="tel:0765042710">📞Call</a>
<a href="https://wa.me/256 765042710">WhatsApp</a>
<a href="sms:0758294286">SMS</a>
</div>

<p class="footer">© Welcome to Wolokoso Saving! Thank you.</p>

</div>

<script src="script.js"></script>
</body>
</html>
<style>
body {
font-family: Arial;
background: #f2f2f2;
}

.container {
width: 90%;
max-width: 400px;
margin: auto;
background: white;
padding: 20px;
border-radius: 15px;
box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

h2 {
text-align: center;
text-decoration: underline;
}

form {
display: flex;
flex-direction: column;
}

input {
padding: 10px;
margin: 5px 0 15px;
border-radius: 8px;
border: 1px solid #ccc;
}

button {
background: green;
color: white;
padding: 12px;
border: none;
border-radius: 8px;
font-size: 16px;
cursor: pointer;
}

button:hover {
background: darkgreen;
}

#preview {
width: 100%;
margin-top: 10px;
border-radius: 10px;
}

.help-box {
background: #eee;
padding: 15px;
margin-top: 10px;
border-radius: 10px;
}

.help-box a {
margin-right: 10px;
color: blue;
text-decoration: none;
}

.footer {
text-align: center;
margin-top: 15px;
font-size: 12px;
}
</style>
<script>
const photoInput = document.getElementById("photo");
const preview = document.getElementById("preview");

// PHOTO PREVIEW
photoInput.addEventListener("change", function () {
const file = this.files[0];

if (file) {
const reader = new FileReader();

reader.onload = function () {
preview.style.display = "block";
preview.src = reader.result;
};

reader.readAsDataURL(file);
}
});

// FORM SUBMIT
document.getElementById("savingForm").addEventListener("submit", function(e){
e.preventDefault();

const form = this;

const formData = {
date: form.date.value,
name: form.name.value,
phone: form.phone.value,
amount: form.amount.value,
};

// SEND TO YOU
emailjs.send("service_y17uayu", "template_ylnzyuf", {
date: formData.date,
name: formData.name,
phone: formData.phone,
amount: formData.amount,
to_email: "mutuyaabdullah849@gmail.com"
})
.then(() => {

// AUTO REPLY TO MEMBER
emailjs.send("service_y17uayu", "template_7pillkf", {
name: formData.name,
email: formData.phone + "@example.com", // optional if no email
message: "Thank you for Saving. Remember saving can change someone's priority."
});

alert("Saved successfully!");
form.reset();
preview.style.display = "none";

}, (error) => {
alert("Failed to send: " + JSON.stringify(error));
});
});
</script>
