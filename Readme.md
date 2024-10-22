# FormTG - Telegram Bot Form Integration

This project demonstrates a simple integration of HTML forms with the Telegram API. By following the instructions below, you can create an HTML form that allows users to submit data, and the submissions will be sent directly to your Telegram chat using the Telegram Bot API.

## Prerequisites

Before you get started, make sure you have the following:

- A Telegram bot created using the [BotFather](https://core.telegram.org/bots#botfather).
- Your Telegram bot token and chat ID.
- A basic understanding of HTML and JavaScript.

## Usage

 **Clone the repository to your local machine:**

   ```bash
   git clone https://github.com/Justcode680/FormTG.git
   ```

1. Open the index.html file in a text editor.

2. Replace the placeholders `'bot_token'` and `'chat_id' `with your actual bot token and chat ID:

```js 
// Replace with your actual bot token and chat ID
var botToken = 'your_bot_token';
var chatId = 'your_chat_id';
```
3. Save the changes.

4. Open the index.html file in a web browser.

5. Fill out the form fields with the desired information.

6. Click the "Submit" button to submit the form.

7. Check your Telegram chat for the form submission message.

# HTML Form
The HTML form is located in the index.html file. Customize the form fields and layout according to your requirements.

```html
<!-- Your HTML Form -->
<form id="contactForm">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required><br>

    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required><br>

    <label for="message">Message:</label>
    <textarea id="message" name="message" rows="4" required></textarea><br>

    <button type="button" onclick="submitForm()">Submit</button>
</form>
```

## JavaScript for Form Submission

The JavaScript code responsible for handling the form submission is also in the `index.html` file. Customize the code as needed.


```html
<script>
function submitForm() {
    var name = document.getElementById("name").value;
    var email = document.getElementById("email").value;
    var message = document.getElementById("message").value;

    var formData = {
        'Name': name,
        'Email': email,
        'Message': message
    };

    // Replace with your actual bot token and chat ID
    var botToken = 'your_bot_token';
    var chatId = 'your_chat_id';

    var htmlMessage = "<b>New Form Submission</b>\n\n";
    for (var key in formData) {
        htmlMessage += "<b>" + key + ":</b> " + formData[key] + "\n";
    }

    var apiUrl = "https://api.telegram.org/bot" + botToken + "/sendMessage";

    var params = {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({
            chat_id: chatId,
            text: htmlMessage,
            parse_mode: 'HTML',
        }),
    };

    fetch(apiUrl, params)
        .then(response => response.json())
        .then(data => {
            console.log('Message sent successfully:', data);
            alert('Message sent successfully!');
        })
        .catch(error => {
            console.error('Error sending message:', error);
            alert('Error sending message. Please try again.');
        });
}
</script>
```

# Conclusion

By following these steps, you can easily integrate HTML forms with the Telegram API, allowing you to receive user submissions directly in your Telegram chat. Feel free to customize the HTML and JavaScript code further based on your specific requirements and design preferences.

Happy coding! 🚀