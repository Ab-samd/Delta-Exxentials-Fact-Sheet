<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DeltaExxentials Product Family | Interactive BoM Builder</title>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root{
--ink:#152331;
--ink-soft:#4b5c6b;
--line:#d8dee3;
--line-soft:#e9edf0;
--paper:#ffffff;
--canvas:#eef1f3;
--navy:#0f2438;
--teal:#0e6e73;
--teal-soft:#e4f1f1;
--amber:#a8631a;
--amber-soft:#faf1e4;
--red:#a3372f;
--red-soft:#fbeae8;
--green:#1e7a4c;
--green-soft:#e7f5ec;
font-size:16px;
}
*{box-sizing:border-box;}
body{
margin:0;
background:var(--canvas);
color:var(--ink);
font-family:"IBM Plex Sans","Segoe UI",Arial,sans-serif;
line-height:1.5;
-webkit-font-smoothing:antialiased;
}
.mono{ font-family:"IBM Plex Mono",Consolas,monospace; }
.sheet{
max-width:920px;
margin:40px auto 80px;
background:var(--paper);
border:1px solid var(--line);
box-shadow:0 1px 3px rgba(15,36,56,0.06), 0 8px 24px rgba(15,36,56,0.04);
}
/* ---- Header ---- */
.letterhead{
background:var(--navy);
color:#eef3f5;
padding:36px 48px 28px;
}
.letterhead .brand{
font-size:0.78rem;
letter-spacing:0.04em;
color:#9fb3c2;
margin-bottom:18px;
}
.letterhead h1{
margin:0 0 6px;
font-size:1.7rem;
font-weight:600;
letter-spacing:-0.01em;
}
.letterhead .sub{
color:#b7c6d1;
font-size:0.98rem;
}
.meta-row{
display:flex;
gap:48px;
margin-top:22px;
padding-top:18px;
border-top:1px solid rgba(255,255,255,0.14);
flex-wrap:wrap;
}
.meta-row div span{
display:block;
font-size:0.72rem;
color:#8fa4b3;
margin-bottom:3px;
}
.meta-row div input{
background:transparent;
border:none;
border-bottom:1px solid rgba(255,255,255,0.3);
color:#eef3f5;
font-size:0.95rem;
font-family:inherit;
padding:2px 0;
width:180px;
}
.meta-row div input::placeholder{ color:#7f93a2; }
/* ---- Sections ---- */
.section{
padding:30px 48px;
border-bottom:1px solid var(--line-soft);
}
.section:last-of-type{ border-bottom:none; }
.section h2{
font-size:0.86rem;
font-weight:600;
color:var(--teal);
letter-spacing:0.02em;
margin:0 0 6px;
display:flex;
align-items:baseline;
gap:10px;
}
.section h2 .num{ color:var(--ink); font-weight:600; }
.section .lede{
font-size:0.85rem;
color:var(--ink-soft);
margin:0 0 18px;
}
/* ---- Field grid (inputs) ---- */
.field-grid{
display:grid;
grid-template-columns:1fr 1fr;
gap:14px 20px;
}
.field-grid.single{ grid-template-columns:1fr; }
.field label{
display:block;
font-size:0.78rem;
color:var(--ink-soft);
margin-bottom:5px;
}
.field .hint{
display:block;
margin-top:4px;
font-size:0.74rem;
color:var(--amber);
}
.field input[type="text"],
.field input[type="email"],
.field input[type="number"],
.field select{
width:100%;
padding:8px 10px;
border:1px solid var(--line);
border-radius:4px;
font-size:0.92rem;
font-family:inherit;
color:var(--ink);
background:#fff;
}
.field input:focus, .field select:focus{
outline:none;
border-color:var(--teal);
box-shadow:0 0 0 3px var(--teal-soft);
}
/* toggle group (Yes/No, contract period, payment option) */
.toggle-group{ display:flex; gap:8px; }
.toggle-group button{
flex:1;
padding:8px 10px;
border:1px solid var(--line);
background:#fff;
color:var(--ink-soft);
font-family:inherit;
font-size:0.88rem;
border-radius:4px;
cursor:pointer;
transition:background 0.12s, border-color 0.12s, color 0.12s;
}
.toggle-group button:hover{ border-color:var(--teal); }
.toggle-group button.active{
background:var(--teal);
border-color:var(--teal);
color:#fff;
font-weight:600;
}
.check-msg{
margin-top:6px;
font-size:0.8rem;
padding:4px 9px;
border-radius:4px;
display:inline-block;
}
.check-msg.ok{ background:var(--green-soft); color:var(--green); }
.check-msg.warn{ background:var(--red-soft); color:var(--red); }
.check-msg.pending{ background:#f2f4f5; color:var(--ink-soft); }
.addon-block{
border:1px solid var(--line-soft);
border-radius:6px;
padding:16px 18px;
margin-bottom:14px;
}
.addon-block:last-child{ margin-bottom:0; }
.addon-block .addon-head{
display:flex;
justify-content:space-between;
align-items:center;
gap:16px;
flex-wrap:wrap;
margin-bottom:0;
}
.addon-block .addon-head strong{ font-size:0.92rem; }
.addon-block .addon-detail{
margin-top:14px;
padding-top:14px;
border-top:1px dashed var(--line-soft);
display:none;
}
.addon-block .addon-detail.shown{ display:grid; grid-template-columns:1fr 1fr; gap:14px 20px; }
/* ---- Tier badge ---- */
.tier-badge{
display:inline-flex;
align-items:center;
gap:10px;
background:var(--teal-soft);
color:var(--teal);
padding:10px 16px;
border-radius:6px;
font-size:0.95rem;
font-weight:600;
}
.tier-badge.out{ background:var(--red-soft); color:var(--red); }
.tier-badge .sku-pill{
font-family:"IBM Plex Mono",monospace;
font-size:0.78rem;
background:#fff;
padding:2px 8px;
border-radius:3px;
font-weight:500;
}
/* ---- Tables ---- */
table{ width:100%; border-collapse:collapse; font-size:0.88rem; }
thead th{
text-align:left;
font-size:0.72rem;
letter-spacing:0.02em;
color:var(--ink-soft);
background:#f5f7f8;
padding:9px 12px;
border-bottom:1px solid var(--line);
border-top:1px solid var(--line);
}
tbody td{
padding:10px 12px;
border-bottom:1px solid var(--line-soft);
vertical-align:top;
}
tbody tr:last-child td{ border-bottom:1px solid var(--line); }
td.num, th.num{ text-align:right; font-family:"IBM Plex Mono",monospace; font-size:0.85rem; }
.sku{
display:inline-block;
background:var(--teal-soft);
color:var(--teal);
padding:1px 7px;
border-radius:3px;
font-size:0.8rem;
font-family:"IBM Plex Mono",monospace;
}
tr.total td{ font-weight:600; background:#f5f7f8; }
.empty-row td{ text-align:center; color:var(--ink-soft); font-style:italic; padding:20px; }
/* ---- Payment summary ---- */
.summary-table td:first-child{ color:var(--ink-soft); }
.summary-table tr.grand td{
font-weight:700;
font-size:0.98rem;
background:var(--teal-soft);
color:var(--navy);
}
/* ---- Terms ---- */
ol.terms{ margin:0; padding-left:20px; font-size:0.85rem; color:var(--ink-soft); }
ol.terms li{ margin-bottom:9px; }
ol.terms li:last-child{ margin-bottom:0; }
.contact-grid{ display:grid; grid-template-columns:repeat(4,1fr); gap:16px; }
.contact-grid div span{ display:block; font-size:0.72rem; color:var(--ink-soft); margin-bottom:3px; }
.confidential{ padding:18px 48px 30px; font-size:0.76rem; color:#8595a1; font-style:italic; }
.reset-bar{
display:flex; justify-content:flex-end; padding:14px 48px 0;
}
.reset-bar button{
background:none; border:1px solid var(--line); color:var(--ink-soft);
font-family:inherit; font-size:0.8rem; padding:6px 12px; border-radius:4px; cursor:pointer;
}
.reset-bar button:hover{ border-color:var(--red); color:var(--red); }
@media (max-width:640px){
.sheet{ margin:0; border:none; }
.letterhead, .section, .confidential, .reset-bar{ padding-left:22px; padding-right:22px; }
.meta-row{ flex-direction:column; gap:10px; }
.field-grid, .addon-block .addon-detail.shown{ grid-template-columns:1fr; }
.contact-grid{ grid-template-columns:1fr 1fr; }
table{ font-size:0.78rem; }
}
</style>
</head>
<body>
<div class="sheet">
<div class="letterhead">
<div class="brand" id="letterheadBrand">DELTA SPIKE ASIA SDN BHD</div>
<h1>DeltaExxentials Product Family</h1>
<div class="sub">Interactive Fact Gathering & BoM Builder</div>
<div class="meta-row">
<div><span>BoM Reference</span><input type="text" id="quoteRef" placeholder="DS-SME-[XXX]"></div>
<div><span>Date of Issue</span><input type="text" id="issueDate" placeholder="DD Month YYYY"></div>
<div><span>Prepared By</span><input type="text" id="preparedBy" placeholder="firstname.lastname"></div>
</div>
</div>
<div class="reset-bar"><button id="resetBtn" type="button">Reset all fields</button></div>

<!-- 0. DEAL TYPE -->
<div class="section">
<h2><span class="num">0.</span> Deal Type</h2>
<div class="field-grid">
<div class="field">
<label>Is this BoM for a Partner or a Direct Client?</label>
<div class="toggle-group" data-group="dealType">
<button type="button" data-value="partner">Partner</button>
<button type="button" data-value="client">Client</button>
</div>
</div>
<div class="field" id="partnerNameField" style="display:none;">
<label>Partner / Reseller Company Name</label>
<input type="text" id="partnerName" placeholder="Enter authorized partner name">
<div id="partnerValidationMsg"></div>
<span class="hint">Must match an authorized partner from the official directory to proceed under Partner pricing.</span>
</div>
</div>
</div>

<!-- 0B. PRODUCT SELECTION -->
<div class="section">
<h2><span class="num">0B.</span> Product Selection</h2>
<div class="toggle-group" data-group="product" style="max-width:480px;">
<button type="button" data-value="x1">DeltaExxentials (Entry)</button>
<button type="button" data-value="x2">DeltaExxentials 2.0 (Advanced)</button>
</div>
<p class="lede" id="productFeatureNote" style="margin-top:14px;">Select a product to see what's included.</p>
</div>

<!-- 1. CUSTOMER DETAILS -->
<div class="section">
<h2><span class="num">1.</span> Customer Details</h2>
<div class="field-grid">
<div class="field"><label>Company Name</label><input type="text" id="companyName"></div>
<div class="field"><label>Point of Contact Name</label><input type="text" id="pocName"></div>
<div class="field"><label>Point of Contact Email</label><input type="email" id="pocEmail"></div>
<div class="field"><label>Company Address</label><input type="text" id="companyAddress"></div>
<div class="field"><label>Total Staff (Headcount)</label><input type="number" id="headcount" min="0"><span class="hint">Optional</span></div>
<div class="field">
<label>Client Origin Country</label>
<select id="clientCountry"><option value="">— select —</option></select>
</div>
<div class="field">
<label>Currency</label>
<input type="text" id="clientCurrency" readonly placeholder="Auto-filled from Country">
<span class="hint">Pricing output dynamically reflects the selected regional equivalent pricing structure.</span>
</div>
</div>
</div>

<!-- 1. SUBSCRIPTION INPUTS -->
<div class="section">
<h2><span class="num">1.</span> Endpoint & Contract Details</h2>
<div class="field-grid">
<div class="field">
<label>Total Endpoint to Subscribe</label>
<input type="number" id="totalEP" min="0">
<span class="hint">Minimum 50, Maximum 200 Endpoints</span>
<div id="epRangeMsg"></div>
</div>
<div class="field"></div>
<div class="field"><label>– Windows Endpoints</label><input type="number" id="winEP" min="0"></div>
<div class="field"><label>– Linux Endpoints</label><input type="number" id="linEP" min="0"></div>
<div class="field"><label>– macOS Endpoints</label><input type="number" id="macEP" min="0"></div>
<div class="field">
<label>Endpoint Breakdown Check</label>
<div id="breakdownCheck" class="check-msg pending">Enter endpoint counts above</div>
</div>
<div class="field">
<label>Contract Period</label>
<div class="toggle-group" data-group="contractPeriod">
<button type="button" data-value="12">12 Months</button>
<button type="button" data-value="24">24 Months</button>
</div>
</div>
<div class="field">
<label>Payment Option</label>
<div class="toggle-group" data-group="paymentOption">
<button type="button" data-value="monthly">Monthly Payment</button>
<button type="button" data-value="full">Full Payment</button>
</div>
</div>
</div>
</div>

<!-- 1B. ADD-ON REQUIREMENTS -->
<div class="section">
<h2><span class="num">1B.</span> Add-On Requirements (Optional)</h2>
<div class="addon-block">
<div class="addon-head">
<strong>Firewall Integration Required?</strong>
<div class="toggle-group" data-group="fwRequired" style="max-width:180px;">
<button type="button" data-value="yes">Yes</button>
<button type="button" data-value="no">No</button>
</div>
</div>
<div class="addon-detail" id="fwDetail">
<div class="field"><label>Total Devices</label><input type="number" id="fwDevices" min="0"></div>
<div class="field"><label>Unit Price (<span class="curr-lbl">USD</span>/Device/Month)</label><div id="fwUnitPriceDisplay" class="check-msg pending" style="display:inline-block;">Enter Total Endpoint to Subscribe</div></div>
</div>
</div>
<div class="addon-block">
<div class="addon-head">
<strong>Email Threat Monitoring Required?</strong>
<div class="toggle-group" data-group="elRequired" id="elToggleGroup" style="max-width:180px;">
<button type="button" data-value="yes">Yes</button>
<button type="button" data-value="no">No</button>
</div>
<span id="elIncludedBadge" class="check-msg ok" style="display:none;">Included in DeltaExxentials 2.0 — no separate charge</span>
</div>
<div class="addon-detail" id="elDetail">
<div class="field">
<label>Email Platform in Use</label>
<select id="emailPlatform">
<option value="">— select —</option>
<option value="ms365">Microsoft 365 with Microsoft Defender P1/P2</option>
<option value="other">Other – Not Supported</option>
</select>
<div id="emailPlatformCheck"></div>
</div>
<div class="field" id="elUnitPriceField"><label>Unit Price (<span class="curr-lbl">USD</span>/Month)</label><div id="elUnitPriceDisplay" class="check-msg pending" style="display:inline-block;">Enter Total Endpoint to Subscribe</div></div>
</div>
</div>
<div class="addon-block">
<div class="addon-head">
<strong>AI Governance (AIDR) Required?</strong>
<div class="toggle-group" data-group="aiRequired" id="aiToggleGroup" style="max-width:180px;">
<button type="button" data-value="yes">Yes</button>
<button type="button" data-value="no">No</button>
</div>
<span id="aiIncludedBadge" class="check-msg ok" style="display:none;">Included in DeltaExxentials 2.0 — no separate charge</span>
</div>
</div>
<div class="addon-block">
<div class="addon-head">
<strong>Additional NGSIEM Beyond Bundled MOQ Required?</strong>
<div class="toggle-group" data-group="addNsRequired" style="max-width:180px;">
<button type="button" data-value="yes">Yes</button>
<button type="button" data-value="no">No</button>
</div>
</div>
<div class="addon-detail" id="nsDetail">
<div class="field"><label>Estimated Additional Log Volume (GB/day)</label><input type="number" id="addNsVolume" min="0"></div>
</div>
</div>
</div>

<!-- 2. SUBSCRIPTION ORDER -->
<div class="section">
<h2><span class="num">2.</span> Subscription Order</h2>
<p class="lede">Tier and SKUs are determined automatically from the details above.</p>
<div id="bundledFeaturesNote" style="display:none; margin-bottom:14px; font-size:0.83rem; color:var(--ink-soft); background:#f5f7f8; border-radius:6px; padding:10px 14px;">
DeltaExxentials 2.0 includes AI Governance, Email Threat Monitoring (M365), Quarterly Business Review, 180-Day Retention and 2 GB/day of NGSIEM log ingestion at no additional charge for the bundle's own usage. Firewall Integration (2 GB/day per unit) and any Additional NGSIEM volume requested are billed in full, on top of that included baseline.
</div>
<div style="margin-bottom:16px;">
<span id="tierBadge" class="tier-badge out">Select a product and enter Total Endpoint to Subscribe</span>
</div>
<table>
<thead>
<tr>
<th>Item</th>
<th>SKU</th>
<th class="num">Endpoint / GB Qty</th>
<th class="num">Unit Price (<span class="curr-lbl">USD</span>)</th>
<th class="num">Line Amount (<span class="curr-lbl">USD</span>/Month)</th>
</tr>
</thead>
<tbody id="orderBody">
<tr class="empty-row"><td colspan="5">No line items yet — complete Section 1 to generate the order.</td></tr>
</tbody>
<tfoot>
<tr class="total">
<td colspan="4">TOTAL MONTHLY SUBSCRIPTION SUBTOTAL (<span class="curr-lbl">USD</span>, excl. SST)</td>
<td class="num" id="subtotalCell">0.00</td>
</tr>
</tfoot>
</table>
</div>

<!-- 3. PAYMENT SUMMARY -->
<div class="section">
<h2><span class="num">3.</span> Payment Summary</h2>
<table class="summary-table">
<tbody>
<tr><td>Monthly Subscription Subtotal (<span class="curr-lbl">USD</span>)</td><td class="num" id="sumSubtotal">0.00</td></tr>
<tr><td>Contract Period Selected</td><td class="num" id="sumContractPeriod">—</td></tr>
<tr><td>Annual Upfront Payment Incentive (5%)</td><td class="num" id="sumDiscount">0.00</td></tr>
<tr id="partnerCommissionRow" style="display:none;"><td>Partner Commission (30%)</td><td class="num" id="sumPartnerCommission">0.00</td></tr>
<tr class="grand"><td>TOTAL CONTRACT VALUE FOR CONTRACT PERIOD</td><td class="num" id="sumContractIncl">0.00</td></tr>
<tr><td>Payment Option Selected</td><td class="num" id="sumPaymentOption">—</td></tr>
<tr class="grand"><td>AMOUNT PAYABLE TODAY</td><td class="num" id="sumTodayIncl">0.00</td></tr>
</tbody>
</table>
<div style="margin-top:20px; padding-top:20px; border-top:1px solid var(--line-soft); display:flex; align-items:center; gap:16px; flex-wrap:wrap;">
<button type="button" id="generateQuoteBtn" style="background:var(--navy); color:#fff; border:none; padding:11px 22px; border-radius:5px; font-family:inherit; font-size:0.9rem; font-weight:600; cursor:pointer;">Generate BoM</button>
<span id="quoteGenMsg"></span>
</div>
<p class="lede" id="partnerSummaryNote" style="margin-top:10px; margin-bottom:0; display:none;">Opens a BoM in a new tab, laid out per DeltaSpike's standard BoM/quotation format. For an authorized Partner, both the BoM and this summary reflect pricing net of the 30% Partner Commission.</p>
<p class="lede" id="clientSummaryNote" style="margin-top:10px; margin-bottom:0;">Opens a BoM in a new tab, laid out per DeltaSpike's standard BoM/quotation format.</p>
</div>

<!-- 4. TERMS AND CONDITIONS -->
<div class="section">
<h2><span class="num">4.</span> Terms and Conditions</h2>
<ol class="terms">
<li>This Fact Gathering Sheet serves as a preliminary BoM for budgetary purposes and does not constitute a binding agreement. A binding commitment is formed only upon execution of the relevant DeltaExxentials or DeltaExxentials 2.0 Statement of Work (SOW) by both parties.</li>
<li>Pricing above is based on the Total Endpoint to Subscribe and Operating System breakdown indicated in Section 1. Final pricing is subject to reconfirmation of Endpoint count during Onboarding.</li>
<li>The Minimum Endpoint Commitment is 50 Endpoints and the Maximum Endpoint Commitment under this BoM is 200 Endpoints. Endpoint counts outside this range require a separate enterprise-scoped quotation.</li>
<li>The Operating System breakdown (Windows, Linux, macOS) is required to prepare the correct EDR sensor package for deployment; inaccurate breakdowns may delay onboarding.</li>
<li>Prices quoted are in selected regional currency. Applicable local taxes and SST will be captured separately in the formal quotation stage.</li>
<li>The Full Payment option requires payment in advance for the entire Contract Period selected. The Monthly Payment option is billed monthly in advance.</li>
<li>A 5% Annual Upfront Payment incentive applies to the Total Contract Value where the Full Payment option is selected.</li>
<li>This BoM is valid for thirty (30) days from the Date of Issue stated above.</li>
<li>DeltaExxentials 2.0 includes AI Governance, Email Threat Monitoring (M365), Quarterly Security Review and 180-Day Retention as standard, at no additional charge. These are optional, separately priced add-ons under DeltaExxentials.</li>
<li>Firewall Integration and, for DeltaExxentials customers, Email Monitoring service fees are computed per the rate-card formula and reflected in Section 2. Add-on services selected in Section 1B form part of the same subscription order.</li>
<li>Firewall Integration requires 2 GB/day of NGSIEM log ingestion for every firewall unit added (e.g. 2 units require 4 GB/day), for both DeltaExxentials and DeltaExxentials 2.0. "Additional NGSIEM" volume is entered as GB/day beyond the bundled MOQ and is billed as entered. Both are billed in full and are never offset by DeltaExxentials 2.0's included 2 GB/day baseline, which covers only the bundle's own Email/AI usage; DeltaExxentials (entry tier) has no included baseline at all, so Firewall Integration, Email Monitoring, and any additional volume requested are all billed in full.</li>
<li>Email Threat Monitoring supports Microsoft 365 and Microsoft Defender telemetry only. Other email platforms are not supported under this offering.</li>
<li id="termPartnerCommission" style="display:none;">A 30% Partner Commission applies where this BoM is issued to an authorized Partner (Section 0).</li>
<li>All pricing in this document reflects regional price structures from the official matrix, defaulting unlisted regions to US region pricing.</li>
<li>The DeltaSpike Group contracting entity, registered office address and named contacts shown in Section 5 (and reflected in the generated BoM) are determined by the Client Origin Country selected in Section 1. This routing affects office/contact details only and has no effect on the currency or pricing shown, which follow the Regional Pricing Matrix independently.</li>
<li>All amounts are indicative until confirmed in a formal quotation or invoice issued by the DeltaSpike Group entity named in Section 5.</li>
</ol>
</div>

<!-- 5. CONTACT -->
<div class="section">
<h2><span class="num">5.</span> <span id="officeSectionHeading">Delta Spike Asia Sdn Bhd</span></h2>
<p class="lede" id="officeRoutingNote" style="margin-top:-6px;">Contracting entity, address and named contacts below are determined by the Client Origin Country selected in Section 1.</p>
<div class="contact-grid">
<div><span>Company</span><span id="officeCompany">Delta Spike Asia Sdn Bhd</span></div>
<div><span>Email</span><span id="officeEmails">tasha.nasir@deltaspike.io<br>chris.beh@deltaspike.io</span></div>
<div><span>Phone</span><span id="officePhone">+60 377 328 975</span></div>
<div><span>Address</span><span id="officeAddress">28-8, Oval Damansara, 685, Jln Damansara, Bukit Kiara, 60000 Kuala Lumpur, Malaysia</span></div>
<div><span>Website</span>www.deltaspike.io</div>
</div>
</div>
<div class="confidential">This document is confidential and intended solely for the use of the addressee named in Section 1.<br>Build: 2026-09-18b — Optional Add-Ons section/table omitted from the generated BoM when no add-on is selected.</div>
</div>

<script>
(function(){
var PARTNER_COMMISSION = 0.30; // 30% partner commission
var AUTHORIZED_PARTNERS = [
"Ask4key", "Bumi Optimus", "Core Memory", "CATO", "CrowdStrike",
"CSM", "CTC", "Ezidea", "EGL", "EN", "Fentons", "Hurricane",
"Imperium", "IshanTech", "JOS", "Monarch", "NTT Data", "Qumulo",
"Reddy", "Starhub", "Strategic Alliance", "Strateq", "Thakral",
"TM", "Time", "Titan System", "ViewQWest"
];

var REGIONAL_PRICING = {
'UK': { currency: 'GBP', x1: { T1: 7.99, T2: 6.99 }, x2: { T1: 12.99, T2: 10.99 } },
'USA': { currency: 'USD', x1: { T1: 9.99, T2: 8.99 }, x2: { T1: 16.99, T2: 14.99 } },
'Australia': { currency: 'AUD', x1: { T1: 15.99, T2: 13.99 }, x2: { T1: 24.99, T2: 22.99 } },
'Sri Lanka': { currency: 'LKR', x1: { T1: 2699.99, T2: 2399.99 }, x2: { T1: 4399.99, T2: 3999.99 } },
'Singapore': { currency: 'SGD', x1: { T1: 13.99, T2: 12.99 }, x2: { T1: 21.99, T2: 19.99 } },
'Malaysia': { currency: 'MYR', x1: { T1: 33.99, T2: 29.99 }, x2: { T1: 54.99, T2: 49.99 } },
'New Zealand': { currency: 'NZD', x1: { T1: 13.99, T2: 12.99 }, x2: { T1: 22.99, T2: 20.99 } }
};
var DEFAULT_REGION = 'USA';

var PRODUCTS = {
x1: {
name: 'DeltaExxentials',
tiers: [
{ code:'T1', min:50,  max:100, sku:'DS-SME-DX1-T1' },
{ code:'T2', min:101, max:200, sku:'DS-SME-DX1-T2' }
]
},
x2: {
name: 'DeltaExxentials 2.0',
tiers: [
{ code:'T1', min:50,  max:100, sku:'DS-SME-DX2-T1' },
{ code:'T2', min:101, max:200, sku:'DS-SME-DX2-T2' }
]
}
};

var ADDON = {
FW: { sku:'DS-SME-ADDFW', label:'Firewall Integration Service' },
EL: { sku:'DS-SME-ADDEL', label:'Email Monitoring Service' },
NS: { sku:'DS-SME-ADDNS', label:'NGSIEM Log Ingestion (Bundled + Additional)', basePriceMYR: 315 },
AI: { sku:'DS-SME-ADDAI', label:'AI Governance (AIDR)', basePriceMYR: 14 }
};

var FX_FROM_MYR = {
'MYR': 1,
'USD': 1 / 4.1,
'GBP': 1 / 5.61,
'AUD': 1 / 2.98,
'LKR': 83.59,
'SGD': 1 / 3.29,
'NZD': 1 / 2.39
};
function convertFromMYR(amountMYR, currency){
var rate = FX_FROM_MYR[currency];
if (rate == null) rate = FX_FROM_MYR.USD;
return amountMYR * rate;
}

var COUNTRIES = [
['United States','USA'], ['United Kingdom','UK'], ['Canada','USA'], ['Mexico','USA'],
['United Arab Emirates','USA'], ['Saudi Arabia','USA'], ['Australia','Australia'],
['Sri Lanka','Sri Lanka'], ['Singapore','Singapore'], ['Malaysia','Malaysia'], ['New Zealand','New Zealand'],
['Afghanistan','USA'], ['Albania','USA'], ['Algeria','USA'], ['Argentina','USA'], ['Austria','USA'],
['Bahrain','USA'], ['Bangladesh','USA'], ['Belgium','USA'], ['Brazil','USA'], ['Brunei','USA'],
['Cambodia','USA'], ['Chile','USA'], ['China','USA'], ['Colombia','USA'], ['Czech Republic','USA'],
['Denmark','USA'], ['Egypt','USA'], ['Finland','USA'], ['France','USA'], ['Germany','USA'],
['Greece','USA'], ['Hong Kong','USA'], ['Hungary','USA'], ['India','USA'], ['Indonesia','USA'],
['Ireland','USA'], ['Israel','USA'], ['Italy','USA'], ['Japan','USA'], ['Jordan','USA'],
['Kenya','USA'], ['Kuwait','USA'], ['Laos','USA'], ['Luxembourg','USA'], ['Macau','USA'],
['Netherlands','USA'], ['Nigeria','USA'], ['Norway','USA'], ['Oman','USA'], ['Pakistan','USA'],
['Philippines','USA'], ['Poland','USA'], ['Portugal','USA'], ['Qatar','USA'], ['Romania','USA'],
['Russia','USA'], ['South Africa','USA'], ['South Korea','USA'], ['Spain','USA'], ['Sweden','USA'],
['Switzerland','USA'], ['Taiwan','USA'], ['Thailand','USA'], ['Turkey','USA'], ['Vietnam','USA'],
['Other / Not Listed','USA']
];

var OFFICES = {
  MY: {
    entity: 'Delta Spike Asia Sdn Bhd',
    address: '28-8, Oval Damansara, 685, Jln Damansara, Bukit Kiara, 60000 Kuala Lumpur, Malaysia',
    phone: '+60 377 328 975',
    emails: ['tasha.nasir@deltaspike.io', 'chris.beh@deltaspike.io']
  },
  SG: {
    entity: 'DeltaSpike Pte Ltd',
    address: '1 Wallich Street, Guoco Tower, Level 14-01, Singapore 078881',
    phone: '+65 63 799 324',
    emails: ['ash.li@deltaspike.io']
  },
  LK: {
    entity: 'DeltaSpike (Pte) Ltd',
    address: 'No. 248, 1st Floor, Thimbirigasyaya Road, Colombo 05, Sri Lanka',
    phone: '+947 698 26 532',
    emails: ['ashan.desilva@deltaspike.io', 'rashad.latiff@deltaspike.io', 'dishni.weerasinghe@deltaspike.io']
  },
  US: {
    entity: 'DeltaSpike Incorporated',
    address: '1500 S Dairy Ashford Rd Suite 355, Houston, Texas 77077, United States of America',
    phone: null,
    emails: ['shihan.annon@deltaspike.io']
  },
  UK: {
    entity: 'DeltaSpike UK',
    address: '66 Paul Street, London, EC2A 4NA, United Kingdom',
    phone: null,
    emails: ['emad.zubaidi@deltaspike.io']
  }
};

var OFFICE_BY_COUNTRY = {
  'Malaysia': 'MY',
  'Singapore': 'SG',
  'Sri Lanka': 'LK',
  'United States': 'US', 'Canada': 'US', 'Mexico': 'US', 'Argentina': 'US',
  'Brazil': 'US', 'Chile': 'US', 'Colombia': 'US',
  'United Kingdom': 'UK', 'Ireland': 'UK', 'France': 'UK', 'Germany': 'UK',
  'Netherlands': 'UK', 'Belgium': 'UK', 'Spain': 'UK', 'Italy': 'UK', 'Portugal': 'UK',
  'Switzerland': 'UK', 'Austria': 'UK', 'Sweden': 'UK', 'Norway': 'UK', 'Denmark': 'UK',
  'Finland': 'UK', 'Poland': 'UK', 'Czech Republic': 'UK', 'Hungary': 'UK', 'Greece': 'UK',
  'Luxembourg': 'UK', 'Romania': 'UK', 'Russia': 'UK', 'Albania': 'UK', 'Turkey': 'UK',
  'United Arab Emirates': 'UK', 'Saudi Arabia': 'UK', 'Qatar': 'UK', 'Kuwait': 'UK',
  'Bahrain': 'UK', 'Oman': 'UK', 'Jordan': 'UK', 'Israel': 'UK',
  'Egypt': 'UK', 'Algeria': 'UK', 'Nigeria': 'UK', 'Kenya': 'UK', 'South Africa': 'UK',
  'Afghanistan': 'MY', 'Bangladesh': 'MY', 'Pakistan': 'MY', 'India': 'MY',
  'Australia': 'MY', 'New Zealand': 'MY', 'Indonesia': 'MY', 'Thailand': 'MY',
  'Vietnam': 'MY', 'Philippines': 'MY', 'Brunei': 'MY', 'Cambodia': 'MY', 'Laos': 'MY',
  'China': 'MY', 'Hong Kong': 'MY', 'Macau': 'MY', 'Taiwan': 'MY', 'Japan': 'MY', 'South Korea': 'MY',
  'Other / Not Listed': 'MY'
};
function officeForCountry(country){
  var key = OFFICE_BY_COUNTRY[country] || 'MY';
  return OFFICES[key];
}
function renderOfficeDetails(country){
  var office = officeForCountry(country);
  $('letterheadBrand').textContent = office.entity.toUpperCase();
  $('officeSectionHeading').textContent = office.entity;
  $('officeCompany').textContent = office.entity;
  $('officeEmails').innerHTML = office.emails.join('<br>');
  $('officePhone').textContent = office.phone || 'See email for contact';
  $('officeAddress').textContent = office.address;
}

var state = {
dealType: null,
product: null,
contractPeriod: null,
paymentOption: null,
fwRequired: null,
elRequired: null,
aiRequired: null,
addNsRequired: null,
country: null,
regionKey: null,
currency: null
};
var lastQuote = null;

function $(id){ return document.getElementById(id); }
function rateCardUnitPrice(totalEP){
return Math.ceil((30 / 0.5 / 12) * totalEP);
}
function fmt(n){
if (!isFinite(n)) n = 0;
return n.toLocaleString('en-US', { minimumFractionDigits:2, maximumFractionDigits:2 });
}
function num(id){
var v = parseFloat($(id).value);
return isNaN(v) ? 0 : v;
}
function esc(s){
return String(s == null ? '' : s).replace(/[&<>"']/g, function(c){
return { '&':'&amp;', '<':'&lt;', '>':'&gt;', '"':'&quot;', "'":'&#39;' }[c];
});
}

(function populateCountries(){
var sel = $('clientCountry');
COUNTRIES.forEach(function(c){
var opt = document.createElement('option');
opt.value = c[0];
var reg = REGIONAL_PRICING[c[1]] ? c[1] : DEFAULT_REGION;
opt.setAttribute('data-region', reg);
opt.setAttribute('data-currency', REGIONAL_PRICING[reg].currency);
opt.textContent = c[0] + ' (' + REGIONAL_PRICING[reg].currency + ')';
sel.appendChild(opt);
});
sel.value = 'United States';
state.country = 'United States';
state.regionKey = 'USA';
state.currency = 'USD';
$('clientCurrency').value = 'USD';
renderOfficeDetails('United States');
})();

$('clientCountry').addEventListener('change', function(){
var sel = $('clientCountry');
var opt = sel.options[sel.selectedIndex];
var reg = opt ? opt.getAttribute('data-region') : DEFAULT_REGION;
var currency = opt ? opt.getAttribute('data-currency') : 'USD';
state.country = sel.value || 'United States';
state.regionKey = REGIONAL_PRICING[reg] ? reg : DEFAULT_REGION;
state.currency = currency || 'USD';
$('clientCurrency').value = state.currency;
document.querySelectorAll('.curr-lbl').forEach(function(el){
el.textContent = state.currency;
});
renderOfficeDetails(state.country);
recalc();
});

document.querySelectorAll('.toggle-group').forEach(function(group){
var key = group.getAttribute('data-group');
group.querySelectorAll('button').forEach(function(btn){
btn.addEventListener('click', function(e){
e.preventDefault();
group.querySelectorAll('button').forEach(function(b){ b.classList.remove('active'); });
btn.classList.add('active');
state[key] = btn.getAttribute('data-value');
onAddonToggleChange(key);
recalc();
});
});
});

function onAddonToggleChange(key){
if (key === 'dealType'){
var isPartner = (state.dealType === 'partner');
$('partnerNameField').style.display = isPartner ? '' : 'none';
if (!isPartner) {
$('partnerName').value = '';
$('partnerValidationMsg').innerHTML = '';
}
}
if (key === 'product'){
var note = $('productFeatureNote');
var isX2 = (state.product === 'x2');
if (state.product === 'x1'){
note.textContent = 'DeltaExxentials: core MDR + EDR, SOC triage and investigation, device control, web blocking, incident response, quarterly reporting.';
} else if (state.product === 'x2'){
note.textContent = 'DeltaExxentials 2.0: MDR + EDR, SOC triage and investigation, device control, web blocking, AI Governance, Email Threat Monitoring (M365), incident response, quarterly reporting, Quarterly Security Review, 180-Day Retention and 2 GB/day of NGSIEM log ingestion.';
}
var elToggleGroup = $('elToggleGroup');
if (elToggleGroup) elToggleGroup.style.display = isX2 ? 'none' : '';
var elIncludedBadge = $('elIncludedBadge');
if (elIncludedBadge) elIncludedBadge.style.display = isX2 ? '' : 'none';
var aiToggleGroup = $('aiToggleGroup');
if (aiToggleGroup) aiToggleGroup.style.display = isX2 ? 'none' : '';
var aiIncludedBadge = $('aiIncludedBadge');
if (aiIncludedBadge) aiIncludedBadge.style.display = isX2 ? '' : 'none';
if (isX2){
$('elDetail').classList.add('shown');
$('elUnitPriceField').style.display = 'none';
} else {
$('elUnitPriceField').style.display = '';
if (state.elRequired !== 'yes') $('elDetail').classList.remove('shown');
}
}
if (key === 'fwRequired'){
$('fwDetail').classList.toggle('shown', state.fwRequired === 'yes');
}
if (key === 'elRequired'){
$('elDetail').classList.toggle('shown', state.elRequired === 'yes');
}
if (key === 'addNsRequired'){
$('nsDetail').classList.toggle('shown', state.addNsRequired === 'yes');
}
}

['totalEP','winEP','linEP','macEP','fwDevices','addNsVolume',
'companyName','pocName','pocEmail','companyAddress','headcount','partnerName',
'quoteRef','issueDate','preparedBy']
.forEach(function(id){ $(id).addEventListener('input', recalc); });

$('partnerName').addEventListener('input', validatePartnerAndRecalc);
$('emailPlatform').addEventListener('change', recalc);

function validatePartnerAndRecalc(){
var partnerInput = $('partnerName').value.trim();
var msgEl = $('partnerValidationMsg');
if (state.dealType === 'partner') {
if (partnerInput === '') {
msgEl.innerHTML = '<span class="check-msg pending">Please enter a partner name</span>';
} else {
var matched = AUTHORIZED_PARTNERS.some(function(p){
return p.toLowerCase() === partnerInput.toLowerCase();
});
if (matched) {
msgEl.innerHTML = '<span class="check-msg ok">Authorized Partner verified</span>';
} else {
msgEl.innerHTML = '<span class="check-msg warn">Invalid partner name. Please choose from the official list.</span>';
}
}
} else {
msgEl.innerHTML = '';
}
recalc();
}

$('resetBtn').addEventListener('click', function(){
document.querySelectorAll('input[type="text"], input[type="email"], input[type="number"]').forEach(function(i){ i.value=''; });
$('emailPlatform').value = '';
$('clientCountry').value = 'United States';
state.country = 'United States';
state.regionKey = 'USA';
state.currency = 'USD';
$('clientCurrency').value = 'USD';
document.querySelectorAll('.curr-lbl').forEach(function(el){ el.textContent = 'USD'; });
renderOfficeDetails('United States');
document.querySelectorAll('.toggle-group button.active').forEach(function(b){ b.classList.remove('active'); });
Object.keys(state).forEach(function(k){ if(k!=='country' && k!=='regionKey' && k!=='currency') state[k]=null; });
lastQuote = null;
$('fwDetail').classList.remove('shown');
$('elDetail').classList.remove('shown');
$('nsDetail').classList.remove('shown');
$('partnerNameField').style.display = 'none';
$('partnerValidationMsg').innerHTML = '';
$('elToggleGroup').style.display = '';
$('elIncludedBadge').style.display = 'none';
$('aiToggleGroup').style.display = '';
$('aiIncludedBadge').style.display = 'none';
$('elUnitPriceField').style.display = '';
$('productFeatureNote').textContent = "Select a product to see what's included.";
$('quoteGenMsg').textContent = '';
$('quoteGenMsg').className = '';
recalc();
});

function findTier(ep){
if (!state.product) return null;
var tiers = PRODUCTS[state.product].tiers;
var regData = REGIONAL_PRICING[state.regionKey] || REGIONAL_PRICING[DEFAULT_REGION];
var productPrices = regData[state.product];
for (var i=0;i<tiers.length;i++){
var t = tiers[i];
if (ep >= t.min && ep <= t.max){
return {
code: t.code,
min: t.min,
max: t.max,
sku: t.sku,
price: productPrices[t.code]
};
}
}
return null;
}

function recalc(){
var totalEP = num('totalEP');
var winEP = num('winEP'), linEP = num('linEP'), macEP = num('macEP');
var hasEPInput = $('totalEP').value !== '';
var curr = state.currency || 'USD';
var isPartner = (state.dealType === 'partner');
var partnerInput = $('partnerName').value.trim();
var isAuthorizedPartner = isPartner && AUTHORIZED_PARTNERS.some(function(p){
return p.toLowerCase() === partnerInput.toLowerCase();
});

// Update conditional visibility for Partner Commission text notes
if (isAuthorizedPartner) {
  $('partnerSummaryNote').style.display = '';
  $('clientSummaryNote').style.display = 'none';
  $('termPartnerCommission').style.display = '';
} else {
  $('partnerSummaryNote').style.display = 'none';
  $('clientSummaryNote').style.display = '';
  $('termPartnerCommission').style.display = 'none';
}

var tierBadge = $('tierBadge');
var tier = null;
var epRangeMsg = $('epRangeMsg');
epRangeMsg.innerHTML = '';
var bundledNote = $('bundledFeaturesNote');
bundledNote.style.display = (state.product === 'x2') ? '' : 'none';

if (!state.product){
tierBadge.className = 'tier-badge out';
tierBadge.textContent = 'Select a product above (Section 0B)';
} else if (!hasEPInput){
tierBadge.className = 'tier-badge out';
tierBadge.textContent = 'Enter Total Endpoint to Subscribe (Section 1)';
} else if (totalEP < 50 || totalEP > 200){
tierBadge.className = 'tier-badge out';
tierBadge.textContent = 'Out of range — requires a separate enterprise-scoped quotation';
epRangeMsg.innerHTML = '<span class="check-msg warn">Endpoint count must be between 50 and 200</span>';
} else {
tier = findTier(totalEP);
tierBadge.className = 'tier-badge';
tierBadge.innerHTML = 'Applicable Product/Tier: <strong>' + PRODUCTS[state.product].name + ' — ' + tier.code + '</strong> <span class="sku-pill">' + tier.sku + '</span> — ' + curr + ' ' + fmt(tier.price) + ' / EP / month';
}

var breakdownEl = $('breakdownCheck');
var anyBreakdownEntered = (winEP || linEP || macEP);
if (!hasEPInput || !anyBreakdownEntered){
breakdownEl.className = 'check-msg pending';
breakdownEl.textContent = 'Enter endpoint counts above';
} else {
var sum = winEP + linEP + macEP;
if (sum === totalEP){
breakdownEl.className = 'check-msg ok';
breakdownEl.textContent = 'Matches Total Endpoint to Subscribe (' + sum + ')';
} else {
breakdownEl.className = 'check-msg warn';
breakdownEl.textContent = 'Breakdown (' + sum + ') does not match Total Endpoint (' + totalEP + ')';
}
}

var isX2 = (state.product === 'x2');
var emailPlatform = $('emailPlatform').value;
var emailPlatformCheck = $('emailPlatformCheck');
var emailPlatformOk = false;
emailPlatformCheck.innerHTML = '';
if (isX2 || state.elRequired === 'yes'){
if (emailPlatform === 'ms365'){
emailPlatformOk = true;
emailPlatformCheck.innerHTML = '<span class="check-msg ok">Supported platform</span>';
} else if (emailPlatform === 'other'){
emailPlatformCheck.innerHTML = '<span class="check-msg warn">Not supported — Email Threat Monitoring only supports Microsoft 365 / Microsoft Defender</span>';
} else {
emailPlatformCheck.innerHTML = '<span class="check-msg pending">Select the email platform in use</span>';
}
}

var emailBilled = (!isX2 && state.elRequired === 'yes' && emailPlatformOk);
var fwActive = (state.fwRequired === 'yes');
var aiBilled = (!isX2 && state.aiRequired === 'yes');
var addNsActive = (state.addNsRequired === 'yes');
var fwDevices = num('fwDevices');

var isFixedPriceRegion = (state.regionKey === 'Malaysia' || state.regionKey === 'Sri Lanka');

var rateUnitMYR = tier ? rateCardUnitPrice(totalEP) : 0;
var rateUnitMYRAdjusted = isFixedPriceRegion ? rateUnitMYR : rateUnitMYR * 1.10;
var rateUnit = tier ? convertFromMYR(rateUnitMYRAdjusted, curr) : 0;
$('fwUnitPriceDisplay').textContent = tier ? (curr + ' ' + fmt(rateUnit)) : 'Enter Total Endpoint to Subscribe';
$('fwUnitPriceDisplay').className = tier ? 'check-msg ok' : 'check-msg pending';
$('elUnitPriceDisplay').textContent = tier ? (curr + ' ' + fmt(rateUnit)) : 'Enter Total Endpoint to Subscribe';
$('elUnitPriceDisplay').className = tier ? 'check-msg ok' : 'check-msg pending';

var lines = [];
var subtotal = 0;
if (tier){
var mdrAmount = totalEP * tier.price;
lines.push({
item: PRODUCTS[state.product].name + ' Subscription',
sku: tier.sku,
qty: totalEP,
unit: tier.price,
amount: mdrAmount
});
subtotal += mdrAmount;
}
if (fwActive && tier){
var fwAmount = fwDevices * rateUnit;
lines.push({
item: ADDON.FW.label,
sku: ADDON.FW.sku,
qty: fwDevices,
unit: rateUnit,
amount: fwAmount
});
subtotal += fwAmount;
}
if (emailBilled && tier){
var elAmount = 1 * rateUnit;
lines.push({
item: ADDON.EL.label,
sku: ADDON.EL.sku,
qty: 1,
unit: rateUnit,
amount: elAmount
});
subtotal += elAmount;
}

var fwGB = (fwActive && tier) ? (2 * fwDevices) : 0;
var emailAddonGB = (emailBilled && tier) ? (tier.code === 'T2' ? 4 : 2) : 0;
var additionalGB = addNsActive ? num('addNsVolume') : 0;
var totalGB = fwGB + emailAddonGB + additionalGB;

var nsPriceMYR = isFixedPriceRegion ? ADDON.NS.basePriceMYR : ADDON.NS.basePriceMYR * 1.10;
var nsUnitPrice = convertFromMYR(nsPriceMYR, curr);
if (totalGB > 0 && tier){
var nsAmount = totalGB * nsUnitPrice;
lines.push({
item: ADDON.NS.label,
sku: ADDON.NS.sku,
qty: totalGB + ' GB/day',
unit: nsUnitPrice,
amount: nsAmount
});
subtotal += nsAmount;
}

var aiPriceMYR = isFixedPriceRegion ? ADDON.AI.basePriceMYR : ADDON.AI.basePriceMYR * 1.10;
var aiUnitPrice = convertFromMYR(aiPriceMYR, curr);
if (aiBilled && tier){
var aiAmount = totalEP * aiUnitPrice;
lines.push({
item: ADDON.AI.label,
sku: ADDON.AI.sku,
qty: totalEP,
unit: aiUnitPrice,
amount: aiAmount
});
subtotal += aiAmount;
}

var body = $('orderBody');
body.innerHTML = '';
if (lines.length === 0){
body.innerHTML = '<tr class="empty-row"><td colspan="5">No line items yet — complete Section 1 to generate the order.</td></tr>';
} else {
lines.forEach(function(l){
var tr = document.createElement('tr');
tr.innerHTML =
'<td>' + l.item + '</td>' +
'<td><span class="sku">' + l.sku + '</span></td>' +
'<td class="num">' + l.qty + '</td>' +
'<td class="num">' + fmt(l.unit) + '</td>' +
'<td class="num">' + fmt(l.amount) + '</td>';
body.appendChild(tr);
});
}
$('subtotalCell').textContent = fmt(subtotal);

var contractMonths = state.contractPeriod ? parseInt(state.contractPeriod, 10) : 0;
var contractExcl = subtotal * contractMonths;
var discount = (state.paymentOption === 'full') ? contractExcl * 0.05 : 0;
var contractExclAfterDiscount = contractExcl - discount;

var partnerCommission = isAuthorizedPartner ? contractExclAfterDiscount * PARTNER_COMMISSION : 0;
var contractIncl = contractExclAfterDiscount - partnerCommission;

var todayExcl = 0;
if (state.paymentOption === 'full'){
todayExcl = contractIncl;
} else if (state.paymentOption === 'monthly'){
var monthlyCommission = isAuthorizedPartner ? subtotal * PARTNER_COMMISSION : 0;
todayExcl = subtotal - monthlyCommission;
}
var todayIncl = todayExcl;

$('sumSubtotal').textContent = fmt(subtotal);
$('sumContractPeriod').textContent = state.contractPeriod ? (state.contractPeriod + ' Months') : '—';
$('sumDiscount').textContent = fmt(discount);
var partnerCommissionRow = $('partnerCommissionRow');
if (isAuthorizedPartner){
partnerCommissionRow.style.display = '';
$('sumPartnerCommission').textContent = fmt(partnerCommission);
} else {
partnerCommissionRow.style.display = 'none';
$('sumPartnerCommission').textContent = fmt(0);
}
$('sumContractIncl').textContent = fmt(contractIncl);
$('sumPaymentOption').textContent = state.paymentOption === 'full' ? 'Full Payment' : (state.paymentOption === 'monthly' ? 'Monthly Payment' : '—');
$('sumTodayIncl').textContent = fmt(todayIncl);

lastQuote = {
tier: tier,
product: state.product ? PRODUCTS[state.product].name : null,
lines: lines,
subtotal: subtotal,
contractMonths: contractMonths,
discount: discount,
partnerCommission: partnerCommission,
contractExclAfterDiscount: contractExclAfterDiscount,
contractIncl: contractIncl,
paymentOptionLabel: state.paymentOption === 'full' ? 'Full Payment' : (state.paymentOption === 'monthly' ? 'Monthly Payment' : null),
todayExcl: todayExcl,
todayIncl: todayIncl,
dealType: state.dealType,
partnerName: partnerInput,
isAuthorizedPartner: isAuthorizedPartner,
companyName: $('companyName').value,
pocName: $('pocName').value,
pocEmail: $('pocEmail').value,
companyAddress: $('companyAddress').value,
country: state.country,
currency: state.currency,
quoteRef: $('quoteRef').value,
issueDate: $('issueDate').value,
preparedBy: $('preparedBy').value,
office: officeForCountry(state.country)
};
}

var LINE_DESCRIPTIONS = {
'DS-SME-DX1-T1': 'DeltaExxentials: core MDR + EDR, SOC triage and investigation, device control, web blocking, incident response, quarterly reporting.',
'DS-SME-DX1-T2': 'DeltaExxentials: core MDR + EDR, SOC triage and investigation, device control, web blocking, incident response, quarterly reporting.',
'DS-SME-DX2-T1': 'DeltaExxentials 2.0: MDR + EDR, SOC triage and investigation, device control, web blocking, AI Governance, Email Threat Monitoring (M365), incident response, quarterly reporting, Quarterly Security Review, 180-Day Retention and 2 GB/day of NGSIEM log ingestion.',
'DS-SME-DX2-T2': 'DeltaExxentials 2.0: SMDR + EDR, SOC triage and investigation, device control, web blocking, AI Governance, Email Threat Monitoring (M365), incident response, quarterly reporting, Quarterly Security Review, 180-Day Retention and 2 GB/day of NGSIEM log ingestion.',
'DS-SME-ADDFW': 'Perimeter security / firewall integration, including policy configuration and ongoing management.',
'DS-SME-ADDEM': 'Post-delivery phishing and Business Email Compromise (BEC) detection — Microsoft 365 and Microsoft Defender telemetry only.',
'DS-SME-ADDNS': 'Log ingestion, correlation and 180-day retention, sized to bundled and additional GB/day requirements.',
'DS-SME-ADDAI': 'Data-loss controls detecting and blocking sensitive or regulated data from reaching external AI models, agents, and third-party AI systems.'
};
var LINE_UOM = {
'DS-SME-ADDFW': 'Device(s)',
'DS-SME-ADDEM': 'Service',
'DS-SME-ADDNS': '',
'DS-SME-ADDAI': 'Endpoint(s)'
};

function quoteRow(l, q, discountPct){
var isBase = q.tier && l.sku === q.tier.sku;
var uom = isBase ? 'Endpoint(s)' : (LINE_UOM[l.sku] || 'Unit(s)');
var desc = LINE_DESCRIPTIONS[l.sku] || '';
var linePct = q.subtotal > 0 ? (l.amount / q.subtotal) : 0;
var totalDeduction = q.discount + (q.partnerCommission || 0);
var lineDeductionShare = totalDeduction * linePct;
var lineTotal = (l.amount * q.contractMonths) - lineDeductionShare;
return (
'<tr><td>' + esc(l.item) + '</td>' +
'<td>' + esc(l.sku) + '</td>' +
'<td class="description">' + esc(desc) + '</td>' +
'<td>' + esc(l.qty) + '</td>' +
'<td>' + esc(uom) + '</td>' +
'<td class="number">' + fmt(l.unit) + '</td>' +
'<td>' + esc(q.contractMonths) + '</td>' +
'<td>Month(s)</td>' +
'<td class="number">' + discountPct + '</td>' +
'<td class="number">' + fmt(lineTotal) + '</td>' +
'<td></td></tr>'
);
}

function buildQuotationHtml(q){
var discountPct = (q.discount > 0 ? '5%' : '0%') + (q.partnerCommission > 0 ? ' + 30%' : '');
var coreLines = q.lines.filter(function(l){ return q.tier && l.sku === q.tier.sku; });
var addonLines = q.lines.filter(function(l){ return !(q.tier && l.sku === q.tier.sku); });
var curr = q.currency || 'USD';
var tableHead =
'<thead><tr><th style="width:40px;">Item</th><th style="width:110px;">SKU</th>' +
'<th style="width:320px;">Description</th><th style="width:60px;">Qty</th>' +
'<th style="width:90px;">UOM</th><th style="width:100px;">Unit Price (' + curr + ')</th>' +
'<th style="width:50px;">Term</th><th style="width:90px;">Term UOM</th>' +
'<th style="width:70px;">Discount</th><th style="width:110px;">Total Price (' + curr + ')</th>' +
'<th style="width:160px;">Remarks</th></tr></thead>';
var coreRows = coreLines.map(function(l){ return quoteRow(l, q, discountPct); }).join('');
var addonRows = addonLines.map(function(l){ return quoteRow(l, q, discountPct); }).join('');
var partnerLine = q.isAuthorizedPartner ? esc(q.partnerName) + ' (Authorized Partner Deal)' : 'Direct / Unverified Partner';
var office = q.office || OFFICES.MY;
var officeEmailsHtml = office.emails.join(' / ');
return '<!DOCTYPE html><html lang="en"><head><meta charset="UTF-8">' +
'<title>BoM \u2014 ' + esc(q.companyName || 'Client') + '</title>' +
'<style>' +
'body{font-family:Verdana,Arial,sans-serif;background:#eef1f3;margin:0;padding:30px;color:#1F3864;}' +
'.doc{max-width:1160px;margin:0 auto;background:#fff;border:1px solid #d8dee3;}' +
'.head{background:#1f2937;padding:18px 24px;}' +
'.head h1{color:#fff;margin:0;font-size:1.4rem;}' +
'.head .sub{color:#c7d0d8;font-size:0.85rem;margin-top:4px;}' +
'.content-section{padding:20px 24px;font-family:Verdana,sans-serif;}' +
'.meta{line-height:1.9;font-size:0.92rem;}' +
'.meta strong{color:#1F3864;}' +
'hr{border:none;height:2px;background-color:#ccc;margin:18px 0;}' +
'h2{color:#1F3864;font-size:1.1rem;}' +
'table{border-collapse:collapse;width:100%;font-size:0.83rem;}' +
'table,th,td{border:1px solid #1F3864;}' +
'th{background:#f5f7f8;color:#1F3864;padding:7px 8px;text-align:left;}' +
'td{padding:7px 8px;color:#1F3864;vertical-align:top;}' +
'td.number, th.number{text-align:right;}' +
'.description{max-width:320px;}' +
'.print-bar{padding:14px 24px;text-align:right;}' +
'.print-bar button{background:#1f2937;color:#fff;border:none;padding:8px 16px;border-radius:4px;cursor:pointer;font-family:inherit;}' +
'@media print{ .print-bar{display:none;} body{background:#fff;padding:0;} .doc{border:none;} }' +
'</style></head><body>' +
'<div class="doc">' +
'<div class="head"><h1>' + esc(office.entity) + '</h1><div class="sub">BoM \u2014 System-Generated from Fact Gathering Sheet</div></div>' +
'<div class="print-bar"><button onclick="window.print()">Print / Save as PDF</button></div>' +
'<div class="content-section">' +
'<h2>BoM</h2>' +
'<div class="meta">' +
'<strong>BoM Reference:</strong> ' + esc(q.quoteRef || '\u2014') + '<br>' +
'<strong>Date of Issue:</strong> ' + esc(q.issueDate || '\u2014') + '<br>' +
'<strong>Prepared By:</strong> ' + esc(q.preparedBy || '\u2014') + '<br>' +
'<strong>Partner:</strong> ' + partnerLine + '<br>' +
'<strong>End User:</strong> ' + esc(q.companyName || '\u2014') + '<br>' +
'<strong>Point of Contact:</strong> ' + esc(q.pocName || '\u2014') + (q.pocEmail ? ' (' + esc(q.pocEmail) + ')' : '') + '<br>' +
'<strong>Company Address:</strong> ' + esc(q.companyAddress || '\u2014') + '<br>' +
'<strong>Client Origin Country:</strong> ' + esc(q.country || '\u2014') + '<br>' +
'<strong>BoM Currency:</strong> ' + curr + ' (Regional Equivalents Matrix)<br>' +
'<strong>Contract Period:</strong> ' + esc(q.contractMonths || '\u2014') + ' Month(s)<br>' +
(q.partnerCommission > 0 ? '<strong>Partner Commission (30%):</strong> -' + curr + ' ' + fmt(q.partnerCommission) + '<br>' : '') +
'<strong>Total Contract Value (excl. applicable local taxes / SST):</strong> ' + curr + ' ' + fmt(q.contractIncl) + '<br>' +
'<strong>Amount Payable Today (excl. applicable local taxes / SST):</strong> ' + curr + ' ' + fmt(q.todayIncl) + '<br>' +
'<strong>Service Line:</strong> ' + esc(q.product || '\u2014') + '<br>' +
'<strong>Contracting Entity:</strong> ' + esc(office.entity) + '<br>' +
'<strong>Registered Office:</strong> ' + esc(office.address) +
'</div>' +
'<hr>' +
'<h2>CORE SERVICES (Quoted Price)</h2>' +
'<table>' + tableHead + '<tbody>' + (coreRows || '<tr><td colspan="11" style="text-align:center;font-style:italic;">No core service line \u2014 confirm Product and Endpoint count</td></tr>') + '</tbody></table>' +
(addonLines.length > 0 ?
'<hr>' +
'<h2>OPTIONAL ADD-ONS (Available Upon Request)</h2>' +
'<table>' + tableHead + '<tbody>' + addonRows + '</tbody></table>'
: '') +
'<hr>' +
'<p>This BoM is system-generated from the Fact Gathering Sheet and is pending Commercial review before being sent to the customer. Applicable local taxes and SST will be captured separately in the formal quotation stage.</p>' +
'<p><strong>Generated on:</strong> ' + esc(new Date().toString()) + '</p>' +
'<p>Questions? Contact your Commercial Team \u2014 ' + esc(officeEmailsHtml) + '</p>' +
'</div></div></body></html>';
}

$('generateQuoteBtn').addEventListener('click', function(){
var msg = $('quoteGenMsg');
if (!lastQuote || lastQuote.lines.length === 0){
msg.className = 'check-msg warn';
msg.textContent = 'Select a Product and enter a valid Total Endpoint to Subscribe (Section 0B / 1) before generating a BoM.';
return;
}
if (!lastQuote.companyName){
msg.className = 'check-msg warn';
msg.textContent = 'Enter Company Name (Section 1) before generating a BoM.';
return;
}
if (!lastQuote.contractMonths){
msg.className = 'check-msg warn';
msg.textContent = 'Select a Contract Period (Section 1) before generating a BoM.';
return;
}
if (!lastQuote.paymentOptionLabel){
msg.className = 'check-msg warn';
msg.textContent = 'Select a Payment Option (Section 1) before generating a BoM.';
return;
}
msg.className = 'check-msg ok';
msg.textContent = 'BoM opened in a new tab.';
var html = buildQuotationHtml(lastQuote);
var win = window.open('', '_blank');
if (!win){
msg.className = 'check-msg warn';
msg.textContent = 'Pop-up blocked — please allow pop-ups for this page and try again.';
return;
}
win.document.open();
win.document.write(html);
win.document.close();
});

recalc();
})();
</script>
</body>
</html>