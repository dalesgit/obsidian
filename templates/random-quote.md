<%*

var quote;
var cite;

async function updateQuote() {
    // Inspired by https://codepen.io/lukePeavey/pen/RwNVeQG
    // Fetch a random quote from the Quotable API
    //const response = await fetch("http://api.quotable.io/random?tags=famous-quotes,inspirational"); // example with tags
    const response = await fetch("http://api.quotable.io/random?tags=");
    const data = await response.json();
    if (response.ok) {
      // Update DOM elements
      quote = data.content;
      cite  = data.author;
    } else {
      quote = "An error occured";
      console.log(data);
    }
  }

await updateQuote();

tR += "> " + quote + "\r\n";
tR += "> -- <cite>" + cite + "</cite>";

%>