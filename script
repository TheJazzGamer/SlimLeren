// Woordenlijsten per taal
const wordLists = {
    frans: ["Bonjour", "Merci", "Au revoir"],
    duits: ["Hallo", "Danke", "Auf Wiedersehen"],
    latijn: ["Salve", "Gratias", "Vale"],
    grieks: ["Χαίρετε", "Ευχαριστώ", "Αντίο"]
};

let selectedLanguages = [];
let words = [];
let currentIndex = 0;
let correctWords = [];
let incorrectWords = [];

function startLearning() {
    const checkboxes = document.querySelectorAll('.language:checked');
    selectedLanguages = Array.from(checkboxes).map(checkbox => checkbox.value);
    
    // Verzamel woorden uit geselecteerde lijsten
    selectedLanguages.forEach(language => {
        words = words.concat(wordLists[language]);
    });

    // Randomize de volgorde van de woorden
    words.sort(() => Math.random() - 0.5);

    // Toon eerste flashcard
    showNextFlashcard();
    
    // Wissel menu en flashcard
    document.getElementById('menu').style.display = 'none';
    document.getElementById('flashcard-container').style.display = 'block';
}

function showNextFlashcard() {
    if (currentIndex < words.length) {
        const word = words[currentIndex];
        document.getElementById('word').textContent = word;
        document.getElementById('translation').textContent = '';
        document.getElementById('feedback').style.display = 'none';
    } else {
        // Alle woorden gevraagd, toon resultaten
        document.getElementById('flashcard-container').style.display = 'none';
        document.getElementById('results').style.display = 'block';
        displayResults();
    }
}

function flipCard() {
    const word = document.getElementById('word').textContent;
    const translation = getTranslation(word);
    document.getElementById('translation').textContent = translation;
}

function markCorrect() {
    correctWords.push(words[currentIndex]);
    currentIndex++;
    showNextFlashcard();
}

function markIncorrect() {
    incorrectWords.push(words[currentIndex]);
    currentIndex++;
    showNextFlashcard();
}

function getTranslation(word) {
    // Hier zou je een vertaling kunnen opzoeken in een woordenboek of API
    // Voor nu retourneren we hetzelfde woord
    return word;
}

function returnToMenu() {
    currentIndex = 0;
    correctWords = [];
    incorrectWords = [];
    selectedLanguages = [];
    words = [];
    document.getElementById('results').style.display = 'none';
    document.getElementById('menu').style.display = 'block';
}

function displayResults() {
    const correctList = document.getElementById('correct-list');
    const incorrectList = document.getElementById('incorrect-list');

    correctWords.forEach(word => {
        const li = document.createElement('li');
        li.textContent = word;
        correctList.appendChild(li);
    });

    incorrectWords.forEach(word => {
        const li = document.createElement('li');
        li.textContent = word;
        incorrectList.appendChild(li);
    });
}
