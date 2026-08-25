<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>SUBWAY Promotion Tracker</title>

<style>
* {
    box-sizing: border-box;
}

:root {
    --green: #00843d;
    --green-light: #00a651;
    --yellow: #f5bd00;

    --bg: #edf3ef;
    --card: rgba(255,255,255,.96);

    --text: #26302b;
    --muted: #707b75;

    --border: #dce5df;

    --danger: #dc3545;
}

/* =========================
   BODY
========================= */

body {
    margin: 0;
    min-height: 100vh;

    font-family:
        Arial,
        "Noto Sans Thai",
        sans-serif;

    color: var(--text);

    background:
        radial-gradient(
            circle at 15% 15%,
            rgba(0,132,61,.08),
            transparent 28%
        ),
        radial-gradient(
            circle at 85% 80%,
            rgba(245,189,0,.07),
            transparent 25%
        ),
        var(--bg);

    overflow-x: hidden;
}

/* =========================
   SUBWAY WATERMARK
========================= */

body::before {
    content: "SUBWAY";

    position: fixed;

    left: 50%;
    top: 55%;

    transform:
        translate(-50%, -50%)
        rotate(-8deg);

    font-size:
        clamp(130px, 18vw, 280px);

    font-weight: 1000;

    letter-spacing: -12px;

    color:
        rgba(0,132,61,.075);

    white-space: nowrap;

    pointer-events: none;

    z-index: 0;
}

body::after {
    content: "";

    position: fixed;

    width: 560px;
    height: 560px;

    left: 50%;
    top: 55%;

    transform:
        translate(-50%, -50%);

    border-radius: 50%;

    border:
        35px solid
        rgba(0,132,61,.018);

    pointer-events: none;

    z-index: 0;
}

/* =========================
   HEADER
========================= */

.header {
    position: relative;
    z-index: 5;

    background:
        rgba(255,255,255,.98);

    border-bottom:
        3px solid var(--green);

    box-shadow:
        0 3px 18px
        rgba(29,55,40,.08);
}

.header-inner {
    width:
        min(1400px, calc(100% - 50px));

    min-height: 92px;

    margin: auto;

    display: flex;

    align-items: center;

    justify-content: space-between;

    gap: 30px;
}

/* =========================
   BRAND
========================= */

.brand {
    display: flex;
    align-items: center;
    gap: 16px;
}

.logo {
    width: 105px;
    height: 52px;

    border-radius: 10px;

    display: flex;
    align-items: center;
    justify-content: center;

    background:
        linear-gradient(
            135deg,
            #00843d,
            #00a651
        );

    color: white;

    font-size: 19px;

    font-weight: 1000;

    letter-spacing: -1px;

    box-shadow:
        0 4px 12px
        rgba(0,132,61,.18);
}

.brand-title {
    font-size: 23px;
    font-weight: 900;
}

.branch-row {
    display: flex;
    align-items: center;
    gap: 7px;

    margin-top: 5px;
}

.branch-name {
    color: var(--green);

    font-size: 14px;

    font-weight: 700;
}

.edit-branch {
    border: none;

    background: transparent;

    color: #8b948f;

    cursor: pointer;

    padding: 3px 6px;

    border-radius: 5px;
}

.edit-branch:hover {
    color: var(--green);
    background: #edf8f1;
}

/* =========================
   DATE
========================= */

.date-control {
    display: flex;
    align-items: center;
    gap: 10px;
}

.date-label {
    color: var(--muted);
    font-size: 13px;
}

.date-control input {
    border:
        1px solid var(--border);

    background: white;

    color: var(--text);

    padding:
        10px 13px;

    border-radius: 9px;

    font-size: 15px;

    outline: none;

    cursor: pointer;
}

.date-control input:focus {
    border-color: var(--green);

    box-shadow:
        0 0 0 3px
        rgba(0,132,61,.08);
}

/* =========================
   PAGE
========================= */

.page {
    position: relative;
    z-index: 1;

    width:
        min(1400px, calc(100% - 50px));

    margin:
        25px auto 50px;
}

/* =========================
   SUMMARY
========================= */

.top-summary {
    display: grid;

    grid-template-columns:
        repeat(3, 1fr);

    gap: 18px;

    margin-bottom: 22px;
}

.summary-card {
    position: relative;

    overflow: hidden;

    background:
        var(--card);

    border:
        1px solid var(--border);

    border-radius: 14px;

    padding:
        20px 23px;

    box-shadow:
        0 5px 18px
        rgba(38,60,46,.055);
}

.summary-card::before {
    content: "";

    position: absolute;

    left: 0;
    top: 0;
    bottom: 0;

    width: 4px;

    background: var(--green);
}

.summary-card.yellow::before {
    background: var(--yellow);
}

.summary-label {
    color: var(--muted);
    font-size: 13px;
}

.summary-number {
    font-size: 30px;
    font-weight: 900;
    margin-top: 6px;
}

.summary-number.green {
    color: var(--green);
}

.summary-number.yellow {
    color: #d39c00;
}

/* =========================
   MAIN GRID
========================= */

.main-grid {
    display: grid;

    grid-template-columns:
        1.35fr 1fr;

    gap: 22px;
}

/* =========================
   CARD
========================= */

.card {
    background:
        var(--card);

    border:
        1px solid var(--border);

    border-radius: 15px;

    box-shadow:
        0 5px 20px
        rgba(38,60,46,.065);

    overflow: visible;
}

.card-header {
    position: relative;

    min-height: 65px;

    padding:
        18px 23px 18px 28px;

    border-bottom:
        1px solid var(--border);

    display: flex;

    align-items: center;

    justify-content: space-between;
}

.card-header::before {
    content: "";

    position: absolute;

    left: 0;
    top: 18px;
    bottom: 18px;

    width: 4px;

    border-radius:
        0 5px 5px 0;

    background: var(--green);
}

.main-grid > .card:nth-child(2)
.card-header::before {
    background: var(--yellow);
}

.card-title {
    font-size: 18px;
    font-weight: 900;
}

.card-subtitle {
    color: var(--muted);
    font-size: 12px;
}

.card-body {
    padding: 21px;
}

/* =========================
   PROMOTION
========================= */

.promotion-grid {
    display: grid;

    grid-template-columns:
        repeat(2, 1fr);

    gap: 14px;
}

.promotion {
    position: relative;

    background:
        rgba(255,255,255,.92);

    border:
        1px solid #dfe8e2;

    border-radius: 12px;

    padding: 16px;

    transition: .15s;
}

.promotion:hover {
    border-color:
        rgba(0,132,61,.35);

    box-shadow:
        0 5px 15px
        rgba(0,132,61,.09);
}

.promotion-top {
    display: flex;

    align-items: flex-start;

    justify-content: space-between;

    gap: 10px;
}

.promotion-name {
    font-size: 18px;
    font-weight: 900;
}

.promotion-count {
    color: var(--muted);

    font-size: 13px;

    margin-top: 3px;
}

.promotion-controls {
    margin-top: 15px;

    display: flex;

    justify-content: center;

    align-items: center;

    gap: 13px;
}

.count-button {
    width: 46px;
    height: 46px;

    border:
        1px solid #c9e4d3;

    border-radius: 10px;

    background:
        #eef8f2;

    color: var(--green);

    font-size: 25px;

    font-weight: bold;

    cursor: pointer;

    transition: .12s;
}

.count-button:hover {
    background: var(--green);

    color: white;

    box-shadow:
        0 4px 10px
        rgba(0,132,61,.18);
}

.count-number {
    width: 55px;

    text-align: center;

    font-size: 29px;

    font-weight: 900;
}

/* =========================
   MENU
========================= */

.menu {
    position: relative;
}

.menu-button {
    border: none;

    background: transparent;

    color: #8b948f;

    font-size: 22px;

    cursor: pointer;

    border-radius: 6px;

    width: 30px;
    height: 30px;
}

.menu-button:hover {
    background: #f0f3f1;
    color: var(--text);
}

.menu-dropdown {
    display: none;

    position: absolute;

    right: 0;
    top: 32px;

    width: 165px;

    background: white;

    border:
        1px solid var(--border);

    border-radius: 9px;

    box-shadow:
        0 10px 30px
        rgba(0,0,0,.12);

    overflow: hidden;

    z-index: 50;
}

.menu-dropdown button {
    width: 100%;

    border: none;

    background: white;

    color: var(--text);

    text-align: left;

    padding:
        11px 13px;

    cursor: pointer;

    font-size: 14px;
}

.menu-dropdown button:hover {
    background: #f3f6f4;
}

.menu-dropdown .danger {
    color: var(--danger);
}

/* =========================
   ADD PROMOTION
========================= */

.add-promotion {
    margin-top: 14px;

    width: 100%;

    padding: 13px;

    border:
        1px dashed #8fc7a3;

    border-radius: 11px;

    background:
        #f0f9f3;

    color: var(--green);

    font-weight: 900;

    cursor: pointer;
}

.add-promotion:hover {
    background: #e5f5ea;
}

/* =========================
   ADDON
========================= */

.addon-input {
    display: flex;
    gap: 9px;
}

.addon-input input {
    flex: 1;

    height: 45px;

    border:
        1px solid #d9e3dd;

    border-radius: 9px;

    padding:
        0 13px;

    font-size: 16px;

    outline: none;
}

.addon-input input:focus {
    border-color: var(--green);

    box-shadow:
        0 0 0 3px
        rgba(0,132,61,.08);
}

.addon-input button {
    border: none;

    background: var(--green);

    color: white;

    padding:
        0 21px;

    border-radius: 9px;

    font-weight: 900;

    cursor: pointer;
}

.addon-input button:hover {
    background: var(--green-light);
}

.addon-list {
    margin-top: 15px;
}

.addon-item {
    display: flex;

    justify-content: space-between;

    align-items: center;

    padding:
        11px 13px;

    background:
        #f7faf8;

    border:
        1px solid #e3ebe6;

    border-radius: 9px;

    margin-bottom: 7px;
}

.addon-price {
    color: #d39c00;

    
