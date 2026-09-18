const state = {
    name: "",
    country: "",
    age: 17,
    personality: "balanced",
    day: 1,
    totalDays: 30,
    hour: 7,
    minute: 30,
    cash: 100,
    debt: 0,
    maxDebt: 500,
    groceries: { meals: 7, drinks: 10 },
    location: "home",
    stats: { health: 100, energy: 100, hunger: 100, hydration: 100, hygiene: 100, mood: 80 },
    skills: { education: 0, social: 0, fitness: 0, work: 0 },
    npcs: [],
    history: [],
    feed: [],
    currentSection: "places",
    ended: false,
};

const COUNTRIES = {
    "United Arab Emirates": { flag: "🇦🇪" },
    Afghanistan: { flag: "🇦🇫" },
    Pakistan: { flag: "🇵🇰" },
    India: { flag: "🇮🇳" },
    Spain: { flag: "🇪🇸" },
};

const PERSONALITIES = {
    balanced: { label: "Pretty balanced" },
    social: { label: "Outgoing" },
    academic: { label: "Studious" },
    ambitious: { label: "Driven" },
    calm: { label: "Easygoing" },
};

const PLACES = [
    { id: "home", emoji: "🏠", name: "Home", desc: "Rest, eat and drink from your groceries, shower, use your phone and watch TV." },
    { id: "school", emoji: "🏫", name: "School", desc: "Study, attend classes, and meet friends." },
    { id: "work", emoji: "💼", name: "Work", desc: "Earn money by working shifts." },
    { id: "gym", emoji: "🏋️", name: "Gym", desc: "Work out to improve fitness and health." },
    { id: "park", emoji: "🌳", name: "Park", desc: "Relax, socialize, and enjoy the outdoors." },
    { id: "mall", emoji: "🛍️", name: "Mall", desc: "Shop, eat out, and hang out with friends." },
    { id: "cafe", emoji: "☕", name: "Café", desc: "Grab a drink, study, or meet people." },
    { id: "hospital", emoji: "🏥", name: "Hospital", desc: "Get medical treatment when sick." },
];

const HOURS = {
    home: [0, 1440], school: [450, 870], work: [540, 1080], gym: [360, 1320],
    park: [360, 1320], mall: [600, 1320], cafe: [420, 1320], hospital: [0, 1440],
};

const JOBS = [
    { title: "Shop Assistant", education: 0, reputation: 0, pay: 55 },
    { title: "Office Assistant", education: 35, reputation: 15, pay: 75 },
    { title: "Sales Representative", education: 20, reputation: 45, pay: 85 },
    { title: "Junior Developer", education: 70, reputation: 20, pay: 110 },
    { title: "Team Coordinator", education: 50, reputation: 70, pay: 125 },
];

const ACTIVITIES = {
    home: [
        { id: "sleep", emoji: "😴", name: "Sleep", cost: 0, time: 480, effects: { energy: 60, health: 5, mood: 5 } },
        { id: "eat", emoji: "🍽️", name: "Eat Meal", cost: 0, time: 30, effects: { hunger: 40, mood: 5 }, grocery: "meals" },
        { id: "drink", emoji: "💧", name: "Drink Water", cost: 0, time: 5, effects: { hydration: 30 }, grocery: "drinks" },
        { id: "shower", emoji: "🚿", name: "Shower", cost: 2, time: 15, effects: { hygiene: 60, mood: 5 } },
        { id: "tv", emoji: "📺", name: "Watch TV", cost: 0, time: 60, effects: { mood: 15, energy: -5 } },
        { id: "phone", emoji: "📱", name: "Use Phone", cost: 0, time: 30, effects: { mood: 8, social: 2 } },
    ],
    school: [
        { id: "class", emoji: "📚", name: "Attend Class", cost: 0, time: 120, effects: { education: 8, energy: -15, mood: -5 } },
        { id: "study", emoji: "📖", name: "Study", cost: 0, time: 90, effects: { education: 10, energy: -10 } },
        { id: "library", emoji: "📕", name: "Library", cost: 0, time: 60, effects: { education: 6, mood: -3 } },
        { id: "socialize", emoji: "🗣️", name: "Socialize", cost: 0, time: 45, effects: { social: 8, mood: 10 } },
    ],
    work: [
        { id: "shift", emoji: "💼", name: "Work Shift", cost: 0, time: 240, effects: { income: 60, energy: -25, mood: -8, work: 5 } },
        { id: "overtime", emoji: "⏰", name: "Overtime", cost: 0, time: 180, effects: { income: 50, energy: -30, mood: -12, work: 4 } },
    ],
    gym: [
        { id: "workout", emoji: "🏋️", name: "Workout", cost: 8, time: 60, effects: { fitness: 10, health: 8, energy: -20, mood: 8 } },
        { id: "cardio", emoji: "🏃", name: "Cardio", cost: 5, time: 45, effects: { fitness: 8, health: 6, energy: -15, mood: 6 } },
    ],
    park: [
        { id: "walk", emoji: "🚶", name: "Take a Walk", cost: 0, time: 30, effects: { mood: 10, health: 3, energy: -5 } },
        { id: "jog", emoji: "🏃", name: "Jog", cost: 0, time: 40, effects: { fitness: 6, health: 5, energy: -15, mood: 8 } },
        { id: "meet", emoji: "👥", name: "Meet Friends", cost: 0, time: 60, effects: { social: 8, mood: 12 } },
    ],
    mall: [
        { id: "shop", emoji: "🛍️", name: "Go Shopping", cost: 30, time: 90, effects: { mood: 20, hygiene: 5 } },
        { id: "foodcourt", emoji: "🍔", name: "Food Court", cost: 15, time: 45, effects: { hunger: 35, mood: 10 } },
        { id: "groceries", emoji: "🛒", name: "Buy Groceries", cost: 45, time: 30, effects: {}, groceryPurchase: true },
        { id: "movie", emoji: "🎬", name: "Watch Movie", cost: 12, time: 120, effects: { mood: 25, energy: -5 } },
    ],
    cafe: [
        { id: "coffee", emoji: "☕", name: "Buy Coffee", cost: 5, time: 20, effects: { energy: 15, hydration: 10, mood: 5 } },
        { id: "cafe_study", emoji: "📖", name: "Study at Café", cost: 5, time: 60, effects: { education: 7, mood: 5 } },
        { id: "cafe_meet", emoji: "💬", name: "Meet Someone", cost: 5, time: 45, effects: { social: 8, mood: 10 } },
    ],
    hospital: [
        { id: "checkup", emoji: "🩺", name: "Checkup", cost: 25, time: 60, effects: { health: 30 } },
        { id: "treat", emoji: "💊", name: "Get Treatment", cost: 40, time: 90, effects: { health: 50, energy: -10 } },
    ],
};

const TRAVEL = [
    ["United Arab Emirates", "🇦🇪", 200], ["Afghanistan", "🇦🇫", 150],
    ["Pakistan", "🇵🇰", 120], ["India", "🇮🇳", 130], ["Spain", "🇪🇸", 180],
];

const NAMES = ["Albert Lalu", "Harshith Pradeep", "Fares Yusuf", "Anand John", "Ryan Matthew", "Mohammed Shamil", "Yahya bin Navas", "Omar Aslam"];
const EMOJIS = ["🙂", "😎", "🤓", "😊", "😄", "🥳", "😌", "🤗"];
const EVENTS = [
    [0.28, "A quiet day gave you some time to clear your head.", "info", { mood: 4 }],
    [0.20, "You found AED 15 on your way home.", "good", {}, 15],
    [0.18, "You caught a small cold. Take it easy today.", "bad", { health: -5, energy: -8 }],
    [0.20, "A friend sent you a funny message. It lifted your mood.", "good", { mood: 7, social: 2 }],
    [0.14, "You had an unexpectedly productive morning.", "good", { energy: 5, mood: 4 }],
];

const clamp = (value, min, max) => Math.max(min, Math.min(max, value));
const money = value => "AED " + Math.round(value).toLocaleString();

function timeText() {
    const suffix = state.hour >= 12 ? "PM" : "AM";
    const hour = state.hour % 12 || 12;
    return hour + ":" + String(state.minute).padStart(2, "0") + " " + suffix;
}

function addFeed(text, type = "info") {
    const item = { day: state.day, time: timeText(), text, type };
    state.feed.unshift(item);
    state.history.push(item);
    state.feed = state.feed.slice(0, 50);
}

function applyEffects(effects = {}) {
    Object.entries(effects).forEach(([key, amount]) => {
        if (key in state.stats) state.stats[key] = clamp(state.stats[key] + amount, 0, 100);
        if (key in state.skills) state.skills[key] = Math.max(0, state.skills[key] + amount);
    });
}

function advanceDay() {
    state.day++;
    applyEffects({ energy: -25, hunger: -25, hydration: -25, hygiene: -15, mood: -10 });
    if (state.stats.hunger < 20) state.stats.health = clamp(state.stats.health - 5, 0, 100);
    if (state.stats.hydration < 20) state.stats.health = clamp(state.stats.health - 5, 0, 100);
    if (state.stats.hygiene < 20) state.stats.health = clamp(state.stats.health - 3, 0, 100);

    if (state.debt > 0) {
        const interest = Math.round(state.debt * 0.05);
        state.debt = clamp(state.debt + interest, 0, state.maxDebt);
        addFeed("Debt interest added: +" + money(interest) + ".", "bad");
    }

    addFeed("Day " + state.day + ". Time to get moving.");
    const event = EVENTS.find(item => Math.random() < item[0]);
    if (event && state.day <= state.totalDays) {
        applyEffects(event[3]);
        if (event[4]) state.cash += event[4];
        addFeed(event[1], event[2]);
    }
    if (state.day > state.totalDays) endGame();
    if (state.location === "school" && state.day > 15) {
        state.location = "home";
        updateLocation();
    }
}

function addMinutes(minutes) {
    state.minute += minutes;
    while (state.minute >= 60) {
        state.minute -= 60;
        state.hour++;
    }
    if (state.hour >= 24) {
        state.hour -= 24;
        advanceDay();
    }
}

function startGame() {
    state.name = document.getElementById("name").value.trim() || "Player";
    state.country = document.getElementById("country").value;
    state.age = clamp(parseInt(document.getElementById("age").value, 10) || 17, 16, 80);
    state.personality = document.getElementById("personality").value;
    state.day = 1; state.hour = 7; state.minute = 30; state.cash = 100; state.debt = 0;
    state.groceries = { meals: 7, drinks: 10 }; state.location = "home"; state.ended = false;
    state.stats = { health: 100, energy: 100, hunger: 100, hydration: 100, hygiene: 100, mood: 80 };
    state.skills = { education: 0, social: 0, fitness: 0, work: 0 };
    state.feed = []; state.history = []; state.currentSection = "places";
    state.npcs = NAMES.map((name, i) => ({ name, emoji: EMOJIS[i], relationship: 20 + Math.floor(Math.random() * 40) }));

    document.getElementById("intro").classList.add("hidden");
    document.getElementById("game").classList.remove("hidden");
    addFeed("You're starting out in " + state.country + ".");
    addFeed("Day 1. You're at home, and there's plenty of time to figure things out.");
    updateLocation();
    render();
}

function updateLocation() {
    const place = PLACES.find(item => item.id === state.location);
    if (!place) return;
    document.getElementById("locationTitle").textContent = place.emoji + " " + place.name;
    document.getElementById("locationDesc").textContent = place.desc;
}

function available(placeId) {
    if (placeId === "school" && state.day > 15) return false;
    if (placeId === "work" && state.day <= 15) return false;
    const [open, close] = HOURS[placeId] || [0, 1440];
    const now = state.hour * 60 + state.minute;
    return open === 0 && close === 1440 || now >= open && now < close;
}

function goTo(placeId) {
    if (state.ended) return;
    const place = PLACES.find(item => item.id === placeId);
    if (!place) return;
    if (state.location === placeId) {
        addFeed("You're already at " + place.name + ".");
    } else if (!available(placeId)) {
        addFeed(place.name + " is closed right now.", "bad");
    } else {
        state.location = placeId;
        addMinutes(15);
        addFeed("You went to " + place.name + ".");
        updateLocation();
    }
    render();
}

function showSection(section) {
    state.currentSection = section;
    ["place", "activity", "travel"].forEach(name => document.getElementById(name + "Tab").classList.toggle("active", section === name + "s"));
    renderMainGrid();
}

function doActivity(id) {
    if (state.ended) return;
    const activity = (ACTIVITIES[state.location] || []).find(item => item.id === id);
    if (!activity) return;
    if (!available(state.location)) return addFeed("This place is closed right now.", "bad"), render();
    if (activity.cost > state.cash) return addFeed("You can't afford that.", "bad"), render();
    if (activity.grocery && state.groceries[activity.grocery] <= 0) return addFeed("You're out of that. Buy more groceries at the mall.", "bad"), render();

    if (activity.grocery) state.groceries[activity.grocery]--;
    if (activity.groceryPurchase) {
        state.groceries.meals += 7;
        state.groceries.drinks += 10;
        addFeed("You bought groceries: 7 meals and 10 drinks.", "good");
    }
    state.cash -= activity.cost;
    applyEffects(activity.effects);
    if (activity.effects.income) {
        const job = getJob();
        const income = activity.id === "shift" ? job.pay : activity.effects.income;
        state.cash += income;
        addFeed("You earned " + money(income) + " as a " + job.title + ".", "good");
    }
    if (state.personality === "academic" && activity.effects.education) state.skills.education += 3;
    if (state.personality === "social" && activity.effects.social) state.skills.social += 3;
    addMinutes(activity.time);
    addFeed(activity.name + " done.");

    if (["socialize", "meet", "cafe_meet"].includes(id)) {
        const npc = state.npcs[Math.floor(Math.random() * state.npcs.length)];
        if (npc) npc.relationship = clamp(npc.relationship + 5, 0, 100);
    }
    checkGameOver();
    render();
}

function getReputation() {
    return state.npcs.length ? Math.round(state.npcs.reduce((sum, npc) => sum + npc.relationship, 0) / state.npcs.length) : 0;
}

function getJob() {
    const qualified = JOBS.filter(job => state.skills.education >= job.education && getReputation() >= job.reputation);
    return qualified[qualified.length - 1] || JOBS[0];
}

function skipDay() {
    if (state.ended) return;
    addFeed("You skipped the rest of the day.");
    applyEffects({ energy: -30, hunger: -30, hydration: -30, hygiene: -20, mood: -15 });
    state.hour = 7; state.minute = 30;
    advanceDay();
    checkGameOver();
    render();
}

function travelTo(country) {
    if (state.ended) return;
    const trip = TRAVEL.find(item => item[0] === country);
    if (!trip) return;
    if (state.country === country) return addFeed("You're already in " + country + "."), render();
    if (state.cash < trip[2]) return addFeed("You can't afford that trip.", "bad"), render();
    state.cash -= trip[2]; state.country = country; addMinutes(240);
    addFeed("You traveled to " + country + ".", "good");
    render();
}

function checkGameOver() {
    if (state.stats.health <= 0) endGame("Your health reached zero. You didn't survive.");
    else if (state.debt >= state.maxDebt) endGame("Your debt reached the maximum. You went bankrupt.");
}

function endGame(reason) {
    if (state.ended) return;
    state.ended = true;
    const verdict = state.skills.education >= state.skills.social && state.skills.education >= state.skills.fitness ? "You found your path through learning." : state.skills.social >= state.skills.fitness ? "You built a life around people." : "You kept pushing and looked after yourself.";
    showModal("🏁 Your Story", "<p>" + (reason || "Thirty days are up. Here's how things turned out.") + "</p><p style='margin-top:14px'><strong>" + verdict + "</strong></p><p style='margin-top:14px'>Cash: <strong>" + money(state.cash) + "</strong><br>Debt: <strong>" + money(state.debt) + "</strong></p><button class='primary' onclick='restartGame()'>START OVER</button>");
}

function showModal(title, content) {
    document.getElementById("modalBox").innerHTML = "<button class='close' onclick='closeModal()'>×</button><h2>" + title + "</h2>" + content;
    document.getElementById("modal").classList.remove("hidden");
}

function closeModal() { document.getElementById("modal").classList.add("hidden"); }

function restartGame() {
    closeModal();
    state.ended = false;
    document.getElementById("game").classList.add("hidden");
    document.getElementById("intro").classList.remove("hidden");
}

function phone() {
    showModal("📱 Phone", "<button class='option' onclick='bankApp()'><span class='opt-title'>🏦 Bank</span><span class='opt-sub'>Check balance and loans</span></button><button class='option' onclick='messagesApp()'><span class='opt-title'>💬 Messages</span><span class='opt-sub'>Chat with friends</span></button><button class='option' onclick='jobsApp()'><span class='opt-title'>💼 Jobs</span><span class='opt-sub'>Look for work</span></button>");
}

function bankApp() {
    let html = "<p>Balance: <strong>" + money(state.cash) + "</strong></p><p>Debt: <strong>" + money(state.debt) + " / " + money(state.maxDebt) + "</strong></p>";
    if (state.debt < state.maxDebt) html += "<button class='option' onclick='takeLoan(50)'>Take AED 50 loan</button><button class='option' onclick='takeLoan(100)'>Take AED 100 loan</button>";
    if (state.debt > 0) html += "<button class='option' onclick='repayLoan()'>Repay debt</button>";
    showModal("🏦 Bank", html);
}

function takeLoan(amount) {
    const actual = Math.min(amount, state.maxDebt - state.debt);
    state.debt += actual; state.cash += actual;
    addFeed("You took a loan of " + money(actual) + ".", "bad"); closeModal(); render();
}

function repayLoan() {
    const amount = Math.min(state.cash, state.debt);
    state.cash -= amount; state.debt -= amount;
    addFeed("You repaid " + money(amount) + " of your debt.", "good"); closeModal(); render();
}

function messagesApp() {
    let html = "";
    state.npcs.forEach(npc => { html += "<button class='option' onclick='chatWith(" + JSON.stringify(npc.name) + ")'><span class='opt-title'>" + npc.emoji + " " + npc.name + "</span><span class='opt-sub'>Relationship: " + npc.relationship + "%</span></button>"; });
    showModal("💬 Messages", html);
}

function chatWith(name) {
    showModal("💬 " + name, "<button class='option' onclick='chatAction(" + JSON.stringify(name) + ", 5)'>😊 Friendly chat (+5)</button><button class='option' onclick='chatAction(" + JSON.stringify(name) + ", 10)'>🎁 Give a gift (+10, costs AED 20)</button><button class='option' onclick='chatAction(" + JSON.stringify(name) + ", -5)'>😒 Be rude (-5)</button>");
}

function chatAction(name, amount) {
    if (amount === 10) {
        if (state.cash < 20) return addFeed("You can't afford a gift right now.", "bad"), render();
        state.cash -= 20;
    }
    const npc = state.npcs.find(item => item.name === name);
    if (npc) npc.relationship = clamp(npc.relationship + amount, 0, 100);
    addFeed("You chatted with " + name + "."); closeModal(); render();
}

function jobsApp() {
    if (state.day <= 15) return showModal("💼 Jobs", "<p>Jobs open up after Day 15. For now, focus on school.</p>");
    const job = getJob();
    showModal("💼 Jobs", "<p>Your best option right now is <strong>" + job.title + "</strong> — AED " + job.pay + " per shift.</p><button class='option' onclick='closeModal();goTo(\"work\")'>Go to work</button>");
}

function historyModal() {
    const html = state.history.length ? state.history.slice().reverse().slice(0, 30).map(item => "<div class='feed-item " + item.type + "'><span class='time-tag'>Day " + item.day + " " + item.time + "</span>" + item.text + "</div>").join("") : "<p>No events yet.</p>";
    showModal("📜 History", html);
}

function friendsModal() {
    const html = state.npcs.map(npc => "<div class='npc-row'><span class='avatar'>" + npc.emoji + "</span><div><div class='npc-name'>" + npc.name + "</div><div class='npc-rel'>Relationship: " + npc.relationship + "%</div></div><div class='rel-bar'><div class='rel-fill' style='width:" + npc.relationship + "%'></div></div></div>").join("");
    showModal("👥 Friends", html || "<p>You haven't met anyone yet.</p>");
}

function render() {
    const country = COUNTRIES[state.country] || { flag: "🌍" };
    document.getElementById("playerName").textContent = state.name;
    document.getElementById("playerCountry").textContent = country.flag + " " + state.country;
    document.getElementById("cash").textContent = money(state.cash);
    document.getElementById("debt").textContent = "Debt: " + money(state.debt) + " / " + money(state.maxDebt);
    document.getElementById("day").textContent = clamp(state.day, 1, state.totalDays) + " / " + state.totalDays;
    document.getElementById("time").textContent = timeText();
    document.getElementById("timeFill").style.width = ((state.hour * 60 + state.minute) / 1440 * 100) + "%";
    document.getElementById("act").textContent = state.day <= 15 ? "ACT I • SCHOOL" : "ACT II • ADULT LIFE";
    renderStats(); renderNPCs(); renderInfo(); renderFeed(); renderMainGrid();
}

function renderStats() {
    const rows = [["health", "Health"], ["energy", "Energy"], ["hunger", "Hunger"], ["hydration", "Hydration"], ["hygiene", "Hygiene"], ["mood", "Mood"]];
    let html = rows.map(([key, label]) => "<div class='stat-row'><span class='label'>" + label + "</span><div class='stat-bar'><div class='fill " + key + "' style='width:" + state.stats[key] + "%'></div></div><span class='value'>" + Math.round(state.stats[key]) + "</span></div>").join("");
    html += "<div style='margin-top:14px;border-top:1px solid var(--line);padding-top:12px;'>" + ["education", "social", "fitness", "work"].map(key => "<div class='stat-row'><span class='label'>" + key[0].toUpperCase() + key.slice(1) + "</span><span class='value'>" + state.skills[key] + "</span></div>").join("") + "</div>";
    document.getElementById("stats").innerHTML = html;
}

function renderNPCs() {
    document.getElementById("npcs").innerHTML = state.npcs.slice(0, 4).map(npc => "<div class='npc-row'><span class='avatar'>" + npc.emoji + "</span><div><div class='npc-name'>" + npc.name + "</div><div class='npc-rel'>" + npc.relationship + "%</div></div><div class='rel-bar'><div class='rel-fill' style='width:" + npc.relationship + "%'></div></div></div>").join("");
}

function renderInfo() {
    const personality = PERSONALITIES[state.personality] || PERSONALITIES.balanced;
    document.getElementById("info").innerHTML = "<div class='info-row'><span>Age</span><span class='val'>" + state.age + "</span></div><div class='info-row'><span>Personality</span><span class='val'>" + personality.label + "</span></div><div class='info-row'><span>Country</span><span class='val'>" + state.country + "</span></div><div class='info-row'><span>Location</span><span class='val'>" + PLACES.find(item => item.id === state.location).name + "</span></div><div class='info-row'><span>Day</span><span class='val'>" + state.day + " / " + state.totalDays + "</span></div>";
}

function renderFeed() {
    const html = state.feed.slice(0, 20).map(item => "<div class='feed-item " + item.type + "'><span class='time-tag'>Day " + item.day + " " + item.time + "</span>" + item.text + "</div>").join("");
    document.getElementById("feed").innerHTML = html || "<p style='color:var(--muted);font-size:13px;'>Nothing much has happened yet.</p>";
}

function renderMainGrid() {
    const grid = document.getElementById("mainGrid");
    document.getElementById("sectionTitle").textContent = state.currentSection[0].toUpperCase() + state.currentSection.slice(1);
    if (state.currentSection === "places") {
        grid.innerHTML = PLACES.filter(place => place.id !== "school" || state.day <= 15).filter(place => place.id !== "work" || state.day > 15).map(place => "<div class='card' onclick='goTo(" + JSON.stringify(place.id) + ")'><div class='emoji'>" + place.emoji + "</div><div class='name'>" + place.name + "</div><div class='sub'>" + (place.id === state.location ? "You are here" : "Visit") + "</div></div>").join("");
    } else if (state.currentSection === "activities") {
        const activities = ACTIVITIES[state.location] || [];
        grid.innerHTML = activities.map(item => "<div class='card' onclick='doActivity(" + JSON.stringify(item.id) + ")'><div class='emoji'>" + item.emoji + "</div><div class='name'>" + item.name + "</div><div class='sub'>" + (item.cost ? money(item.cost) : "Free") + " • " + (item.time / 60).toFixed(1) + "h</div></div>").join("");
    } else {
        grid.innerHTML = TRAVEL.map(([country, emoji, cost]) => "<div class='card' onclick='travelTo(" + JSON.stringify(country) + ")'><div class='emoji'>" + emoji + "</div><div class='name'>" + country + "</div><div class='sub'>" + (country === state.country ? "Current" : money(cost)) + "</div></div>").join("");
    }
}

document.addEventListener("DOMContentLoaded", () => {
    document.getElementById("name").focus();
});
