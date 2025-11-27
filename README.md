# Inspirational-Quote-Generator Microservice
This microservice provides a random inspirational quote containing both a quote and an author. It is designed to be consumed by a calling application through a simple REST API.

## Create and Installation 
1. Create .env file
```ini
PORT=YOURPORTNUMBER
DATAFILE=./data/quotes.json
```
2. Install dependencies:
```bash
npm install
```
3. Start the server:
```bash
npm start
```
When server starts, you will see something like this 
Loaded <number> quotes
Server listening on port YOURPORTNUMBER...

**Rest API** 
path: http://localhost:${PORT}/get/quote
method: GET
format: 
```JSON 
{
    "quote": "The most important thing is to try and inspire people so that they can be great in whatever they want to do",
    "author": "Kobe Bryant"
}
```

## Usage
How to fetch the microservice
```javascript
const getQuote = async () => {
    const response = await fetch('/get/quote', {
        method: 'GET',
        headers: { 'Content-Type': 'application/json' }
    });

    const data = await response.json();

    if (response.status === 200) {
        setQuote(data.quote.quote);
        setAuthor(data.quote.author);
    } else {
        console.log("Failed to fetch quote: " + response.status);
    }
};
```
How to display it in react
```javascript
{quote && (
    <div className="quote-container">
        <p className="quote-text">{quote}</p>
        <p className="quote-author">- {author}</p>
        <button onClick={getQuote} className="genQuote">
            Generate New Quote
        </button>
    </div>
)}
```
