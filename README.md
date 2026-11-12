# live-dashboard
[index.html](https://github.com/user-attachments/files/34742128/index.html)
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>MatchDesk | Live Betting Exchange & Admin Panel</title>
<style>
:root{--bg:#070b0e;--panel:#101820;--panel2:#182430;--line:#263847;--txt:#f1f5f9;--muted:#94a3b8;--green:#10b981;--blue:#0ea5e9;--red:#ef4444;--gold:#f59e0b}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--txt);font:14px Arial,sans-serif;background-image:radial-gradient(circle at 10% 20%, rgba(16, 185, 129, 0.04) 0%, transparent 40%), radial-gradient(circle at 90% 80%, rgba(14, 165, 233, 0.04) 0%, transparent 40%)}
header{height:65px;background:#05080a;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;padding:0 24px;position:sticky;top:0;z-index:10;box-shadow:0 4px 20px rgba(0,0,0,0.5)}
.logo{font-size:22px;font-weight:900;letter-spacing:.5px;display:flex;align-items:center;gap:8px}.logo span{color:var(--green)}
.muted{color:var(--muted)}.tag{padding:7px 12px;border:1px solid var(--line);border-radius:20px;background:var(--panel2);font-size:12px;font-weight:600}
.layout{display:grid;grid-template-columns:230px 1fr;gap:18px;max-width:1450px;margin:auto;padding:18px}
nav,.panel{background:var(--panel);border:1px solid var(--line);border-radius:12px;box-shadow:0 8px 24px rgba(0,0,0,0.3)}
nav{padding:14px;height:max-content;position:sticky;top:82px}
nav .navtitle{font-size:11px;color:var(--muted);letter-spacing:1.5px;padding:8px;text-transform:uppercase;font-weight:700}
nav button{display:flex;align-items:center;gap:10px;width:100%;text-align:left;background:transparent;color:var(--txt);padding:12px 14px;border-radius:8px;margin:3px 0;font-weight:600;cursor:pointer;border:0;transition:all .2s ease}
nav button.active,nav button:hover{background:var(--panel2);color:var(--green);transform:translateX(4px)}
main{min-width:0}
.warning{padding:12px 16px;background:linear-gradient(135deg, #1e293b, #0f172a);color:#fbbf24;border:1px solid #d97706;border-radius:10px;margin-bottom:16px;font-weight:500;box-shadow:0 4px 12px rgba(0,0,0,0.2)}
.view{display:none}.view.active{display:block}
.heading{display:flex;justify-content:space-between;align-items:center;gap:12px;margin:4px 0 16px;flex-wrap:wrap}
h1{font-size:24px;margin:0;font-weight:800}h3{font-size:16px;margin:0 0 14px;font-weight:700;display:flex;align-items:center;gap:8px}
.panel{padding:18px;margin-bottom:16px}
.match{border:1px solid var(--line);border-radius:10px;margin:12px 0;overflow:hidden;background:#0d131a}
.matchtop{padding:12px 16px;background:#141f2a;display:flex;justify-content:space-between;gap:10px;align-items:center;border-bottom:1px solid var(--line)}
.matchbody{padding:14px}
.teams{display:flex;justify-content:space-between;gap:12px;margin-bottom:14px}
.team{font-weight:800;font-size:15px}.score{font-size:13px;color:var(--muted);margin-top:4px}
.odds{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px}
.odd{padding:12px;border-radius:8px;border:1px solid var(--line);cursor:pointer;color:white;text-align:center;transition:all .2s}
.odd.back{background:linear-gradient(135deg, #0e374f, #134e6f);border-color:#2563eb}.odd.lay{background:linear-gradient(135deg, #581c25, #7f1d1d);border-color:#dc2626}
.odd:hover{opacity:.9;transform:scale(1.02)}
.odd.selected{outline:2px solid var(--gold);box-shadow:0 0 12px rgba(245, 158, 11, 0.4)}
.odd b{display:block;font-size:18px;margin-top:4px}.odd small{font-size:11px;color:#cbd5e1;font-weight:700;letter-spacing:.5px}
.grid2{display:grid;grid-template-columns:minmax(0,1fr) 320px;gap:16px}
.field{margin:12px 0}.field label{display:block;font-size:12px;color:var(--muted);margin-bottom:6px;font-weight:600}
input,select{width:100%;padding:11px 14px;background:#05080a;color:var(--txt);border:1px solid var(--line);border-radius:8px;font-size:14px}
input:focus,select:focus{outline:1px solid var(--green);border-color:var(--green)}
button{border:0;border-radius:8px;padding:10px 14px;background:var(--green);color:#022c22;font-weight:800;cursor:pointer;transition:all .2s}
button:hover{filter:brightness(1.1)}
button.secondary{background:#334155;color:white}button.danger{background:#dc2626;color:white}button.info{background:#0284c7;color:white}
button:disabled{opacity:.4;cursor:not-allowed}.full{width:100%}
.stats{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}
.stat{padding:14px;background:#080d12;border-radius:10px;border:1px solid var(--line)}.stat small{color:var(--muted);font-weight:600}.stat strong{display:block;font-size:20px;margin-top:6px;color:var(--green)}
table{width:100%;border-collapse:collapse;font-size:13px}td,th{text-align:left;padding:12px 10px;border-bottom:1px solid var(--line)}th{color:var(--muted);font-weight:700}
.scroll{overflow:auto}.status{color:var(--gold);font-weight:700}
.loginbox{max-width:440px;margin:80px auto;background:var(--panel);border:1px solid var(--line);padding:30px;border-radius:16px;box-shadow:0 12px 40px rgba(0,0,0,0.6)}
.loginbox p{line-height:1.6}
.notice{font-size:12px;color:var(--muted);line-height:1.6}
footer{text-align:center;color:var(--muted);font-size:12px;padding:24px}

/* Modal Popup Styles */
.modal{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.7);z-index:100;justify-content:center;align-items:center}
.modal-content{background:var(--panel);border:1px solid var(--line);padding:24px;border-radius:12px;width:420px;max-width:90%;box-shadow:0 10px 30px rgba(0,0,0,0.8)}
@media(max-width:850px){.layout{grid-template-columns:1fr}nav{position:static;display:flex;overflow:auto;gap:4px}nav .navtitle{display:none}nav button{white-space:nowrap;width:auto}.grid2{grid-template-columns:1fr}}
</style>
</head>
<body>

<header>
    <div class="logo">🏏 MATCH<span>DESK</span> <span style="font-size:12px;background:#1e293b;color:#38bdf8;padding:2px 8px;border-radius:6px;border:1px solid #334155">EXCHANGE</span></div>
    <div style="display:flex;gap:10px;align-items:center">
        <span class="tag" id="roleTag">DEMO</span>
        <span class="tag" id="userTag">Not signed in</span>
        <button class="secondary" id="logoutBtn" onclick="logout()" style="display:none;padding:7px 14px;font-size:12px">Logout</button>
    </div>
</header>

<div class="layout" id="app" style="display:none">
    <nav>
        <div class="navtitle">Menu</div>
        <button class="active" data-view="cricket" onclick="showView('cricket',this)">🏏 Live Exchange</button>
        <button data-view="mybets" onclick="showView('mybets',this)">📊 My Bets History</button>
        <button data-view="adminUsers" id="adminUsersNav" onclick="showView('adminUsers',this)" style="display:none">👥 Manage Client IDs</button>
        <button data-view="adminLogs" id="adminLogsNav" onclick="showView('adminLogs',this)" style="display:none">📡 Live Bets Monitor</button>
    </nav>

    <main>
        <div class="warning"><b>⚡ LIVE ADMIN PANEL:</b> Create clients, modify password/limits, check remaining balances & view individual history.</div>

        <!-- Live Matches View -->
        <section class="view active" id="cricket">
            <div class="heading">
                <div><h1>Live Sports Exchange</h1><div class="muted">Real-time virtual odds · Back & Lay markets</div></div>
                <span class="tag" style="background:#451a03;color:#fbbf24;border-color:#b45309">🔥 MARKET LIVE</span>
            </div>
            <div class="grid2">
                <div class="panel">
                    <h3>🏆 Active Featured Matches</h3>
                    
                    <div class="match">
                        <div class="matchtop">
                            <div><b>India vs Australia</b><div class="muted" style="font-size:12px;margin-top:2px">ICC T20 World Series</div></div>
                            <span style="color:#ef4444;font-weight:700">● LIVE</span>
                        </div>
                        <div class="matchbody">
                            <div class="teams">
                                <div><div class="team">🇮🇳 India</div><div class="score">164/4 (16.2 ov)</div></div>
                                <div style="text-align:right"><div class="team">🇦🇺 Australia</div><div class="score">Target: 185</div></div>
                            </div>
                            <div class="odds">
                                <div class="odd back" onclick="choose(this,'India (Ind vs Aus)','BACK',1.68)"><small>BACK</small><b>1.68</b></div>
                                <div class="odd lay" onclick="choose(this,'India (Ind vs Aus)','LAY',1.72)"><small>LAY</small><b>1.72</b></div>
                                <div class="odd back" onclick="choose(this,'Australia (Ind vs Aus)','BACK',2.35)"><small>BACK</small><b>2.35</b></div>
                                <div class="odd lay" onclick="choose(this,'Australia (Ind vs Aus)','LAY',2.42)"><small>LAY</small><b>2.42</b></div>
                            </div>
                        </div>
                    </div>

                    <div class="match">
                        <div class="matchtop">
                            <div><b>England vs Pakistan</b><div class="muted" style="font-size:12px;margin-top:2px">ODI Series</div></div>
                            <span style="color:#ef4444;font-weight:700">● LIVE</span>
                        </div>
                        <div class="matchbody">
                            <div class="teams">
                                <div><div class="team">🏴󠁧󠁢󠁥󠁮󠁧󠁿 England</div><div class="score">288/7 (45.0 ov)</div></div>
                                <div style="text-align:right"><div class="team">🇵🇰 Pakistan</div><div class="score">Yet to bat</div></div>
                            </div>
                            <div class="odds">
                                <div class="odd back" onclick="choose(this,'England (Eng vs Pak)','BACK',1.90)"><small>BACK</small><b>1.90</b></div>
                                <div class="odd lay" onclick="choose(this,'England (Eng vs Pak)','LAY',1.95)"><small>LAY</small><b>1.95</b></div>
                                <div class="odd back" onclick="choose(this,'Pakistan (Eng vs Pak)','BACK',2.02)"><small>BACK</small><b>2.02</b></div>
                                <div class="odd lay" onclick="choose(this,'Pakistan (Eng vs Pak)','LAY',2.10)"><small>LAY</small><b>2.10</b></div>
                            </div>
                        </div>
                    </div>

                </div>

                <aside>
                    <div class="panel">
                        <h3>📥 Bet Slip</h3>
                        <div class="tag" id="chosen" style="margin-bottom:12px;text-align:center">Select odds to place bet</div>
                        <div class="field"><label>Selection</label><input id="runner" readonly value="—"></div>
                        <div class="field"><label>Side</label><input id="side" readonly value="—"></div>
                        <div class="field"><label>Odds</label><input id="price" readonly value="—"></div>
                        <div class="field"><label>Stake (₹)</label><input id="stake" type="number" min="1" value="500"></div>
                        <p class="notice" style="margin-bottom:14px">Potential return: <b id="potential" style="color:var(--green)">—</b> points</p>
                        <button class="full" id="placeBtn" onclick="placeBet()" disabled>Place Bet Now</button>
                    </div>
                    <div class="panel">
                        <h3>💰 Account Summary</h3>
                        <div class="stats">
                            <div class="stat"><small>Remaining Balance (₹)</small><strong id="bal">0</strong></div>
                            <div class="stat"><small>Placed Bets</small><strong id="betcount" style="color:var(--blue)">0</strong></div>
                        </div>
                    </div>
                </aside>
            </div>
        </section>

        <!-- My Bets View -->
        <section class="view" id="mybets">
            <div class="heading"><h1>My Placed Bets History</h1></div>
            <div class="panel scroll">
                <table>
                    <thead><tr><th>Time</th><th>Selection</th><th>Side</th><th>Odds</th><th>Stake (₹)</th><th>Return (₹)</th><th>Status</th></tr></thead>
                    <tbody id="myBetRows"></tbody>
                </table>
            </div>
        </section>

        <!-- Admin: Manage Users View -->
        <section class="view" id="adminUsers">
            <div class="heading"><div><h1>Client ID Manager</h1><div class="muted">Create accounts, modify limits, change passwords & view history</div></div></div>
            <div class="panel">
                <h3>➕ Create New Client ID</h3>
                <div style="display:grid;grid-template-columns:1fr 1fr 1fr auto;gap:12px;align-items:end">
                    <div class="field" style="margin:0"><label>Username</label><input id="newU" placeholder="e.g. client02"></div>
                    <div class="field" style="margin:0"><label>Password</label><input id="newP" placeholder="Password"></div>
                    <div class="field" style="margin:0"><label>Starting Balance (₹)</label><input id="newB" type="number" value="10000"></div>
                    <button onclick="createClient()">Create ID</button>
                </div>
                <div id="createMsg" style="color:var(--green);margin-top:10px;font-size:12px;font-weight:600"></div>
            </div>
            <div class="panel">
                <h3>📋 Active Client Accounts</h3>
                <div class="scroll">
                    <table>
                        <thead><tr><th>Username</th><th>Role</th><th>Remaining Balance (₹)</th><th>Actions</th></tr></thead>
                        <tbody id="userTableRows"></tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- Admin: All Bets Logs View -->
        <section class="view" id="adminLogs">
            <div class="heading"><h1>Live Client Bets Monitor</h1><div class="muted">Real-time tracking of all client betting activity</div></div>
            <div class="panel scroll">
                <table>
                    <thead><tr><th>Time</th><th>Client ID</th><th>Selection</th><th>Side</th><th>Odds</th><th>Stake (₹)</th><th>Potential Return (₹)</th></tr></thead>
                    <tbody id="adminBetRows"></tbody>
                </table>
            </div>
        </section>
    </main>
</div>

<!-- Modify Client Modal -->
<div id="modifyModal" class="modal">
    <div class="modal-content">
        <h3>⚙️ Modify Client: <span id="modUsername" style="color:var(--green)"></span></h3>
        <div class="field">
            <label>New Password</label>
            <input id="modPass" placeholder="Leave blank to keep current">
        </div>
        <div class="field">
            <label>Remaining Balance / Limit (₹)</label>
            <input id="modBal" type="number">
        </div>
        <div style="display:flex;gap:10px;margin-top:16px">
            <button class="full" onclick="saveClientModification()">Save Changes</button>
            <button class="full secondary" onclick="closeModifyModal()">Cancel</button>
        </div>
    </div>
</div>

<!-- Client History Modal -->
<div id="historyModal" class="modal">
    <div class="modal-content" style="width:650px">
        <h3>📜 Bet History: <span id="histUsername" style="color:var(--blue)"></span></h3>
        <div class="scroll" style="max-height:300px;margin:12px 0">
            <table>
                <thead><tr><th>Time</th><th>Selection</th><th>Side</th><th>Odds</th><th>Stake (₹)</th><th>Return (₹)</th></tr></thead>
                <tbody id="clientHistoryRows"></tbody>
            </table>
        </div>
        <button class="full secondary" onclick="closeHistoryModal()">Close</button>
    </div>
</div>

<!-- Login Screen -->
<div id="login" class="loginbox">
    <h1 style="margin-bottom:6px;display:flex;align-items:center;gap:10px">🏏 MatchDesk Login</h1>
    <p class="muted" style="margin-bottom:20px">Login with Admin credentials to manage accounts, or use Client IDs created by admin.</p>
    <div class="field"><label>Username</label><input id="loginUser" value="admin"></div>
    <div class="field"><label>Password</label><input id="loginPass" type="password" value="admin123"></div>
    <button class="full" onclick="login()" style="margin-top:12px">Sign In to Exchange</button>
    <div class="notice" style="margin-top:16px"><b>Default Admin:</b> admin / admin123</div>
    <div id="loginError" style="color:#ef4444;margin-top:10px;font-weight:600"></div>
</div>

<footer>MatchDesk Exchange & Admin Panel · Live Simulation Demo</footer>

<script>
if(!localStorage.getItem('md_users')){
    localStorage.setItem('md_users', JSON.stringify({
        'admin': {pass: 'admin123', role: 'admin', balance: 0},
        'client01': {pass: 'pass123', role: 'client', balance: 10000}
    }));
}
if(!localStorage.getItem('md_bets')){
    localStorage.setItem('md_bets', JSON.stringify([]));
}

let currentUser = null, selected = null, editingUser = null;

function getUsers(){ return JSON.parse(localStorage.getItem('md_users')); }
function saveUsers(u){ localStorage.setItem('md_users', JSON.stringify(u)); }
function getBets(){ return JSON.parse(localStorage.getItem('md_bets')); }
function saveBets(b){ localStorage.setItem('md_bets', JSON.stringify(b)); }

function login(){
    let u = document.getElementById('loginUser').value.trim();
    let p = document.getElementById('loginPass').value;
    let users = getUsers();

    if(!users[u] || users[u].pass !== p){
        document.getElementById('loginError').textContent = 'Invalid username or password.';
        return;
    }

    currentUser = {username: u, ...users[u]};
    document.getElementById('login').style.display = 'none';
    document.getElementById('app').style.display = 'grid';
    document.getElementById('logoutBtn').style.display = 'inline-block';
    document.getElementById('userTag').textContent = currentUser.username;
    document.getElementById('roleTag').textContent = currentUser.role.toUpperCase();

    let isAdmin = (currentUser.role === 'admin');
    document.getElementById('adminUsersNav').style.display = isAdmin ? 'block' : 'none';
    document.getElementById('adminLogsNav').style.display = isAdmin ? 'block' : 'none';

    if(isAdmin){
        showView('adminLogs', document.querySelector('[data-view="adminLogs"]'));
        renderAdmin();
    } else {
        showView('cricket', document.querySelector('[data-view="cricket"]'));
        renderClient();
    }
}

function logout(){
    currentUser = null;
    document.getElementById('app').style.display = 'none';
    document.getElementById('login').style.display = 'block';
    document.getElementById('logoutBtn').style.display = 'none';
    document.getElementById('loginError').textContent = '';
}

function showView(id, btn){
    document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));
    if(btn) btn.classList.add('active');
    if(currentUser?.role === 'admin' && id.startsWith('admin')) renderAdmin();
    if(currentUser?.role === 'client' || id === 'cricket' || id === 'mybets') renderClient();
}

function choose(el, runner, side, odds){
    document.querySelectorAll('.odd').forEach(x => x.classList.remove('selected'));
    el.classList.add('selected');
    selected = {runner, side, odds};
    document.getElementById('chosen').textContent = runner + ' · ' + side;
    document.getElementById('runner').value = runner;
    document.getElementById('side').value = side;
    document.getElementById('price').value = odds.toFixed(2);
    document.getElementById('placeBtn').disabled = false;
    calc();
}

function calc(){
    let s = Number(document.getElementById('stake').value) || 0;
    document.getElementById('potential').textContent = (selected && s > 0) ? (s * selected.odds).toFixed(2) : '—';
}
document.getElementById('stake').addEventListener('input', calc);

function placeBet(){
    let users = getUsers();
    let balance = users[currentUser.username].balance;
    let s = Number(document.getElementById('stake').value);

    if(!selected || s < 1 || s > balance || !Number.isFinite(s)){
        alert('Invalid stake amount or insufficient remaining balance.');
        return;
    }

    users[currentUser.username].balance -= s;
    saveUsers(users);
    currentUser.balance = users[currentUser.username].balance;

    let bets = getBets();
    bets.unshift({
        time: new Date().toLocaleTimeString(),
        client: currentUser.username,
        ...selected,
        stake: s,
        return: (s * selected.odds).toFixed(2)
    });
    saveBets(bets);

    document.getElementById('placeBtn').disabled = true;
    alert('Bet placed successfully!');
    renderClient();
}

function renderClient(){
    let users = getUsers();
    if(!currentUser || currentUser.role === 'admin') return;
    currentUser.balance = users[currentUser.username].balance;

    document.getElementById('bal').textContent = currentUser.balance.toLocaleString();
    let myBets = getBets().filter(b => b.client === currentUser.username);
    document.getElementById('betcount').textContent = myBets.length;
    
    document.getElementById('myBetRows').innerHTML = myBets.map(b => `
        <tr>
            <td>${b.time}</td>
            <td>${b.runner}</td>
            <td>${b.side}</td>
            <td>${b.odds.toFixed(2)}</td>
            <td>₹${b.stake}</td>
            <td>₹${b.return}</td>
            <td class="status">MATCHED</td>
        </tr>
    `).join('') || '<tr><td colspan="7" class="muted">No bets placed yet.</td></tr>';
}

function createClient(){
    let u = document.getElementById('newU').value.trim();
    let p = document.getElementById('newP').value;
    let b = Number(document.getElementById('newB').value) || 10000;
    let msg = document.getElementById('createMsg');

    if(!u || !p){
        msg.style.color = 'var(--red)';
        msg.textContent = 'Username and password cannot be empty.';
        return;
    }

    let users = getUsers();
    if(users[u]){
        msg.style.color = 'var(--red)';
        msg.textContent = 'Username already exists!';
        return;
    }

    users[u] = {pass: p, role: 'client', balance: b};
    saveUsers(users);
    msg.style.color = 'var(--green)';
    msg.textContent = `Client ID "${u}" created successfully!`;
    document.getElementById('newU').value = '';
    document.getElementById('newP').value = '';
    renderAdmin();
}

function openModifyModal(username){
    let users = getUsers();
    if(!users[username]) return;
    editingUser = username;
    document.getElementById('modUsername').textContent = username;
    document.getElementById('modPass').value = '';
    document.getElementById('modBal').value = users[username].balance;
    document.getElementById('modifyModal').style.display = 'flex';
}

function closeModifyModal(){
    document.getElementById('modifyModal').style.display = 'none';
    editingUser = null;
}

function saveClientModification(){
    if(!editingUser) return;
    let users = getUsers();
    let newPass = document.getElementById('modPass').value.trim();
    let newBal = Number(document.getElementById('modBal').value);

    if(isNaN(newBal)){
        alert('Please enter a valid balance.');
        return;
    }

    if(newPass !== ''){
        users[editingUser].pass = newPass;
    }
    users[editingUser].balance = newBal;
    saveUsers(users);
    closeModifyModal();
    renderAdmin();
    alert(`Client ${editingUser} modified successfully!`);
}

function openHistoryModal(username){
    document.getElementById('histUsername').textContent = username;
    let bets = getBets().filter(b => b.client === username);
    
    document.getElementById('clientHistoryRows').innerHTML = bets.map(b => `
        <tr>
            <td>${b.time}</td>
            <td>${b.runner}</td>
            <td>${b.side}</td>
            <td>${b.odds.toFixed(2)}</td>
            <td>₹${b.stake}</td>
            <td>₹${b.return}</td>
        </tr>
    `).join('') || '<tr><td colspan="6" class="muted">No betting history found for this client.</td></tr>';
    
    document.getElementById('historyModal').style.display = 'flex';
}

function closeHistoryModal(){
    document.getElementById('historyModal').style.display = 'none';
}

function deleteClient(username){
    if(username === 'admin') return;
    if(confirm(`Are you sure you want to delete client ${username}?`)){
        let users = getUsers();
        delete users[username];
        saveUsers(users);
        renderAdmin();
    }
}

function renderAdmin(){
    let users = getUsers();
    let bets = getBets();

    document.getElementById('userTableRows').innerHTML = Object.keys(users).map(u => `
        <tr>
            <td><b>${u}</b></td>
            <td>${users[u].role.toUpperCase()}</td>
            <td>₹${users[u].balance.toLocaleString()}</td>
            <td>
                ${u !== 'admin' ? `
                    <button class="info" style="padding:6px 10px;font-size:11px;margin-right:4px" onclick="openModifyModal('${u}')">Modify</button>
                    <button class="secondary" style="padding:6px 10px;font-size:11px;margin-right:4px" onclick="openHistoryModal('${u}')">History</button>
                    <button class="danger" style="padding:6px 10px;font-size:11px" onclick="deleteClient('${u}')">Delete</button>
                ` : '—'}
            </td>
        </tr>
    `).join('');

    document.getElementById('adminBetRows').innerHTML = bets.map(b => `
        <tr>
            <td>${b.time}</td>
            <td><b>${b.client}</b></td>
            <td>${b.runner}</td>
            <td>${b.side}</td>
            <td>${b.odds.toFixed(2)}</td>
            <td>₹${b.stake}</td>
            <td>₹${b.return}</td>
        </tr>
    `).join('') || '<tr><td colspan="7" class="muted">No bets placed by clients yet.</td></tr>';
}
</script>
</body>
</html>
