<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Global Flagship Education Counseling Dashboard</title>
    
    <!-- Leaflet Structural Map Core Framework -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    
    <style>
        :root {
            --bg-workspace: #0B0F19;
            --bg-panel: #131B2E;
            --bg-card: #1E293B;
            --text-main: #F8FAFC;
            --text-muted: #94A3B8;
            --border-glow: #334155;
            
            /* Cinematic Brand Neon Colors */
            --color-usa: #3B82F6;       /* Electric Blue */
            --color-canada: #EF4444;    /* Crimson Red */
            --color-uk: #A855F7;        /* Neon Purple */
            --color-australia: #10B981; /* Emerald Green */
            --color-nz: #F59E0B;        /* Cyber Amber */
        }

        body {
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            height: 100vh;
            background-color: var(--bg-workspace);
            color: var(--text-main);
            overflow: hidden;
        }

        /* Split-Screen Dashboard Configuration */
        #map-container {
            flex: 1.5;
            height: 100%;
            position: relative;
        }

        #map {
            width: 100%;
            height: 100%;
            background-color: #070A13; /* Cyber Navy Ocean */
        }

        #counseling-sidebar {
            flex: 1.3;
            background: var(--bg-panel);
            box-shadow: -10px 0 40px rgba(0, 0, 0, 0.5);
            display: flex;
            flex-direction: column;
            border-left: 2px solid var(--border-glow);
            z-index: 1000;
        }

        /* Banner branding section inside panel workspace */
        .sidebar-header {
            background: #090D16;
            padding: 24px;
            border-bottom: 1px solid var(--border-glow);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .sidebar-header h1 {
            margin: 0;
            font-size: 1.4rem;
            font-weight: 800;
            letter-spacing: -0.5px;
            background: linear-gradient(90deg, #60A5FA, #A78BFA);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .live-status-tag {
            font-size: 0.75rem;
            background: #1E293B;
            border: 1px solid #10B981;
            color: #10B981;
            padding: 4px 10px;
            border-radius: 20px;
            font-weight: 700;
            text-transform: uppercase;
        }

        .panel-viewport {
            padding: 24px;
            overflow-y: auto;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }

        /* Highly Advanced Dynamic UI Tabs */
        .tab-bar {
            display: flex;
            background: #090D16;
            padding: 4px;
            border-radius: 8px;
            margin-bottom: 24px;
            border: 1px solid var(--border-glow);
        }

        .tab-btn {
            flex: 1;
            background: none;
            border: none;
            padding: 10px;
            color: var(--text-muted);
            font-size: 0.85rem;
            font-weight: 600;
            cursor: pointer;
            border-radius: 6px;
            transition: all 0.2s ease;
        }

        .tab-btn:hover {
            color: var(--text-main);
        }

        .tab-btn.active-tab {
            background: var(--bg-card);
            color: #FFFFFF;
            box-shadow: 0 4px 12px rgba(0,0,0,0.25);
        }

        .tab-content-pane {
            display: none;
            animation: fadeIn 0.3s ease-in-out;
        }

        .tab-content-pane.active-pane {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(5px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Core Dynamic Profile Typographies */
        .state-banner {
            margin-bottom: 20px;
        }

        .state-title {
            font-size: 2.4rem;
            font-weight: 800;
            margin: 0;
            line-height: 1.1;
            letter-spacing: -1px;
        }

        .country-indicator {
            font-size: 0.85rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            margin-top: 6px;
        }

        /* Financial Progress Bar Infrastructure */
        .metric-progress-wrapper {
            margin-bottom: 20px;
        }

        .metric-label-row {
            display: flex;
            justify-content: space-between;
            font-size: 0.8rem;
            font-weight: 700;
            color: var(--text-muted);
            margin-bottom: 6px;
            text-transform: uppercase;
        }

        .progress-track {
            height: 10px;
            background: #090D16;
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid var(--border-glow);
        }

        .progress-fill {
            height: 100%;
            border-radius: 20px;
            width: 0%;
            transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
        }

        /* Multi-Colored Profile Card Elements */
        .premium-card {
            background: var(--bg-card);
            border-radius: 12px;
            padding: 16px;
            margin-bottom: 16px;
            border: 1px solid var(--border-glow);
            position: relative;
        }

        .premium-card::before {
            content: '';
            position: absolute;
            left: 0;
            top: 12px;
            bottom: 12px;
            width: 4px;
            border-radius: 0 4px 4px 0;
            background: currentColor;
        }

        .card-tag {
            font-size: 0.7rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: var(--text-muted);
            margin-bottom: 4px;
        }

        .card-value {
            font-size: 1rem;
            font-weight: 500;
            line-height: 1.5;
            margin: 0;
        }

        /* Premium Highly Detailed University Layouts */
        .uni-card {
            background: #151D30;
            border-radius: 10px;
            border: 1px solid var(--border-glow);
            margin-bottom: 16px;
            overflow: hidden;
        }

        .uni-top-bar {
            background: #0D1321;
            padding: 14px 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--border-glow);
        }

        .uni-title-text {
            font-weight: 700;
            font-size: 1.05rem;
            margin: 0;
        }

        .uni-global-rank {
            font-size: 0.75rem;
            background: #2563EB;
            color: #FFFFFF;
            padding: 3px 8px;
            border-radius: 4px;
            font-weight: 700;
        }

        .uni-content-grid {
            padding: 16px;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 14px;
        }

        .grid-item-full {
            grid-column: span 2;
        }

        .grid-caption {
            font-size: 0.7rem;
            font-weight: 700;
            text-transform: uppercase;
            color: var(--text-muted);
            margin-bottom: 3px;
        }

        .grid-data-value {
            font-size: 0.88rem;
            margin: 0;
            line-height: 1.4;
        }

        /* Welcome Workspace Block */
        .workspace-placeholder {
            text-align: center;
            margin: auto 0;
            padding: 40px 20px;
            border: 2px dashed var(--border-glow);
            border-radius: 16px;
            background: #090D16;
        }

        .workspace-placeholder h3 {
            font-size: 1.3rem;
            margin: 0 0 10px 0;
            color: #FFFFFF;
        }

        .workspace-placeholder p {
            color: var(--text-muted);
            font-size: 0.9rem;
            line-height: 1.6;
            margin: 0;
        }

        /* Custom Vector Map Overlay Labels */
        .leaflet-tooltip.neon-map-label {
            background-color: #090D16;
            color: #FFFFFF;
            border: 1px solid var(--border-glow);
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
            font-weight: 700;
            border-radius: 6px;
            padding: 6px 12px;
            font-size: 0.8rem;
        }
    </style>
</head>
<body>

    <!-- Left Screen Workspace: Dark Theme Core Map Layout -->
    <div id="map-container">
        <div id="map"></div>
    </div>

    <!-- Right Screen Framework: Interactive Data Workspace -->
    <div id="counseling-sidebar">
        <div class="sidebar-header">
            <h1>Counseling Terminal</h1>
            <span class="live-status-tag">Global Framework Active</span>
        </div>
        
        <div class="panel-viewport" id="workspace-viewport">
            <div class="workspace-placeholder">
                <h3>Global Corridor Mapping Engine</h3>
                <p>Click inside any of the neon-highlighted regional sectors across the **USA, Canada, the UK, Australia, or New Zealand** to populate nested institutional records and strategic selling metrics.</p>
            </div>
        </div>
    </div>

    <!-- Map Scripts and GeoJSON Processors -->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

    <script>
        // 1. Initialize Dark-Themed World Vector Canvas
        const map = L.map('map', {
            center: [26, 8],
            zoom: 2.5,
            minZoom: 2,
            maxZoom: 7,
            worldCopyJump: true
        });

        // Use clean dark tiles to make the custom neon borders look striking
        L.tileLayer('https://{s}.basemaps.cartocdn.com/dark_all/{z}/{x}/{y}{r}.png', {
            attribution: '&copy; CARTO Cyber Map Engine'
        }).addTo(map);

        // 2. High-Fidelity Counseling Knowledge Base Mapped to Regional States/Provinces
        const premiumDb = {
            "California": {
                country: "United States of America",
                signatureColor: "var(--color-usa)",
                tuitionIndex: 85, // Scale out of 100 for visual progress bars
                livingIndex: 90,
                tuitionText: "$35,000 - $62,000 USD / Academic Year",
                livingText: "$19,000 - $27,000 USD / Year (Premium Urban Overhead)",
                strategicFactors: [
                    { label: "Silicon Valley Tech Nexus", detail: "Direct pipeline access into global technological conglomerates. Exceptional framework for high-tier STEM OPT job recruitment." },
                    { label: "Public Tier-1 Out-of-State Scaling", desc: "UC system public universities enforce strong non-resident fee premiums. Critical variable during parent budgetary profiling sessions." }
                ],
                universities: [
                    { name: "Stanford University", ranking: "QS World #5", fees: "$64,200 USD/Yr", living: "Est. $2,300/mo", pivot: "Unmatched venture capital incubation access. Direct engineering recruitment into top global accelerators." },
                    { name: "UC Berkeley", ranking: "QS World #12", fees: "$46,500 USD/Yr", living: "Est. $2,100/mo", pivot: "The world's premier public research model. Unrivaled compute infrastructure and deep machine learning labs." }
                ],
                visaRoute: "F-1 Academic Visa Track. Demands I-20 Form clearance and passing a mock-interview panel evaluating intent and spontaneous liquidity ratios."
            },
            "Ontario": {
                country: "Canada",
                signatureColor: "var(--color-canada)",
                tuitionIndex: 70,
                livingIndex: 75,
                tuitionText: "$25,000 - $55,000 CAD / Academic Year",
                livingText: "$18,500 - $24,500 CAD / Year (Reflects updated regulatory GIC updates)",
                strategicFactors: [
                    { label: "Canada's Economic Hub", detail: "Contains over 40% of Canada's total workforce footprint, yielding maximum post-study work placement density." },
                    { label: "OINP Competitive Scaling", desc: "Ontario Immigrant Nominee Program holds competitive scoring. Master's graduate streams provide clear ways to bypass employer requirements." }
                ],
                universities: [
                    { name: "University of Toronto", ranking: "QS World #21", fees: "$51,000 - $64,000 CAD", living: "Est. $1,950/mo", pivot: "Global research heavy hitter. Outstanding prestige metrics across medical engineering, financial mathematics, and deep learning." },
                    { name: "University of Waterloo", ranking: "QS World #112", fees: "$44,000 - $56,000 CAD", living: "Est. $1,600/mo", pivot: "North America's premier structural co-op model. Guarantees real Canadian industry exposure integrated directly into the degree track." }
                ],
                visaRoute: "Study Permit Track. Employs priority processing lines where advanced upfront investments in GIC certificates clear local immigration hurdles fast."
            },
            "Greater London": {
                country: "United Kingdom",
                signatureColor: "var(--color-uk)",
                tuitionIndex: 78,
                livingIndex: 95,
                tuitionText: "£18,500 - £42,000 GBP / Academic Year",
                livingText: "£15,600 - £22,000 GBP / Year (Mandatory high-tier threshold for London perimeter)",
                strategicFactors: [
                    { label: "Global Corporate Nexus", detail: "Unrivaled networking exposure. Direct contact lines into major European technical, design, and financial trading markets." },
                    { label: "12-Month High-ROI Master's", desc: "The UK's unique 1-year postgraduate framework significantly reduces overall living costs compared to typical 2-year routes." }
                ],
                universities: [
                    { name: "Imperial College London", ranking: "QS World #2", fees: "£38,000 - £49,500 GBP", living: "Est. £1,800/mo", pivot: "Elite world-ranked STEM powerhouse. Direct research pipelines into deep technology spin-outs and venture development systems." }
                ],
                visaRoute: "Points-Based Student Visa. Heavily dependent on securing an explicit Confirmation of Acceptance for Studies (CAS) from a tier-4 sponsor."
            },
            "New South Wales": {
                country: "Australia",
                signatureColor: "var(--color-australia)",
                tuitionIndex: 75,
                livingIndex: 85,
                tuitionText: "$32,000 - $52,000 AUD / Academic Year",
                livingText: "$29,710 AUD / Year (Matches modernized statutory proof-of-savings levels)",
                strategicFactors: [
                    { label: "APAC Enterprise Capital", detail: "Sydney houses regional headquarters for most global enterprise operations, optimizing professional internships." },
                    { label: "Metropolitan Work Limitations", desc: "Standard baseline Subclass 485 work permit time frames apply without regional metropolitan extension points." }
                ],
                universities: [
                    { name: "University of Sydney", ranking: "QS World #18", fees: "$48,000 - $56,000 AUD", living: "Est. $2,450/mo", pivot: "Elite employability tracking metrics. Outstanding global institutional standing paired with extensive management networks." },
                    { name: "UNSW Sydney", ranking: "QS World #19", fees: "$49,000 - $54,000 AUD", living: "Est. $2,400/mo", pivot: "Highly technical engineering campus. World pioneer in solar engineering, quantum architectures, and industrial incubation." }
                ],
                visaRoute: "Student Visa (Subclass 500). Subject to rigorous evaluation frameworks under Genuine Student (GS) processing guidelines."
            },
            "Auckland": {
                country: "New Zealand",
                signatureColor: "var(--color-nz)",
                tuitionIndex: 65,
                livingIndex: 70,
                tuitionText: "$30,000 - $48,000 NZD / Academic Year",
                livingText: "$22,000 - $27,500 NZD / Year (Standard localized metrics)",
                strategicFactors: [
                    { label: "Dominant National Infrastructure", detail: "Commercial capital holding roughly one-third of the country's population, making it the highest-density job market." },
                    { label: "Green List Fast-Tracking", desc: "Direct residency pathways are available for engineering and software graduates who match high-demand industry skill definitions." }
                ],
                universities: [
                    { name: "University of Auckland", ranking: "QS World #65", fees: "$40,000 - $48,000 NZD", living: "Est. $2,150/mo", pivot: "New Zealand's premium national research campus. Highly active entrepreneurial ecosystems and startup incubator networks." }
                ],
                visaRoute: "Fee-Paying Student Visa. Requires upfront settlement of first-year educational invoices prior to structural immigration deployment."
            }
        };

        // 3. Cinematic Cyber-Color Coordinate Mapper
        const eliteStudyNations = ["United States of America", "Canada", "Australia", "United Kingdom", "New Zealand"];

        function designVectorLayout(feature) {
            const country = feature.properties.admin;
            const name = feature.properties.name;
            const hasData = premiumDb.hasOwnProperty(name);

            let borderGlow = '#1E293B';
            let fillPalette = '#0D1321';
            let opacity = 0.3;
            let weight = 0.5;

            if (eliteStudyNations.includes(country)) {
                fillPalette = '#1E293B'; // Highlight active target nations
                opacity = 0.6;
                weight = 1;
                borderGlow = '#475569';
                
                if (hasData) {
                    // Apply deep visual neon identifiers for mapped premium regions
                    weight = 2;
                    opacity = 0.85;
                    borderGlow = '#FFFFFF';
                    if (name === 'California') fillColor = '#2563EB';
                    else if (name === 'Ontario') fillPalette = '#DC2626';
                    else if (name === 'Greater London') fillPalette = '#9333EA';
                    else if (name === 'New South Wales') fillPalette = '#059669';
                    else if (name === 'Auckland') fillPalette = '#D97706';
                }
            }

            return {
                fillColor: fillPalette,
                weight: weight,
                opacity: 1,
                color: borderGlow,
                fillOpacity: opacity
            };
        }

        // 4. Interactive Hover Scaling Controllers
        function targetRegionHover(e) {
            const props = e.target.feature.properties;
            if (eliteStudyNations.includes(props.admin)) {
                const layer = e.target;
                layer.setStyle({
                    fillOpacity: 0.95,
                    weight: 3,
                    color: '#FFFFFF'
                });
                layer.bringToFront();
            }
        }

        function targetRegionOut(e) {
            cyberBoundaryLayer.resetStyle(e.target);
        }

        // 5. Advanced Dashboard Viewport Controller
        function targetRegionClick(e) {
            const props = e.target.feature.properties;
            const name = props.name;
            const data = premiumDb[name];
            const viewport = document.getElementById('workspace-viewport');

            if (!data) {
                // Modular fail-safe block for alternate unmapped sub-states
                viewport.innerHTML = `
                    <div class="state-banner">
                        <h2 class="state-title" style="color:#FFF;">${name}</h2>
                        <div class="country-indicator" style="color:#60A5FA;">${props.admin} Sector</div>
                    </div>
                    <div class="premium-card" style="color:var(--text-muted);">
                        <p><strong>Counseling Insight:</strong> This area provides alternate sub-regional options inside ${props.admin}.</p>
                        <p>Perfect for candidates looking to reduce living overheads, target specialized local fields, or utilize non-metropolitan post-study work extension points.</p>
                    </div>
                `;
                return;
            }

            // Animate map focal shift
            map.panTo(e.target.getBounds().getCenter());

            // Build out robust university cards dynamically
            let uniCards = data.universities.map(uni => `
                <div class="uni-card">
                    <div class="uni-top-bar">
                        <h4 class="uni-title-text">${uni.name}</h4>
                        <span class="uni-global-rank">${uni.ranking}</span>
                    </div>
                    <div class="uni-content-grid">
                        <div>
                            <div class="grid-caption">Tuition Matrix</div>
                            <p class="grid-data-value" style="color:#60A5FA; font-weight:700;">${uni.fees}</p>
                        </div>
                        <div>
                            <div class="grid-caption">Local Living</div>
                            <p class="grid-data-value">${uni.living}</p>
                        </div>
                        <div class="grid-item-full">
                            <div class="grid-caption">Strategic Placement Advantage</div>
                            <p class="grid-data-value" style="color:var(--text-main); font-size:0.85rem;">${uni.pivot}</p>
                        </div>
                    </div>
                </div>
            `).join('');

            // Build structural counselor target factors
            let factorsHtml = data.strategicFactors.map(f => `
                <div class="premium-card" style="color:${colorHexValue(name)};">
                    <div class="card-tag">Strategic Variable</div>
                    <h4 class="card-value" style="color:#FFF; margin-bottom:4px;">${f.label}</h4>
                    <p style="margin:0; font-size:0.88rem; color:var(--text-muted); line-height:1.4;">${f.detail || f.desc}</p>
                </div>
            `).join('');

            // Inject structural layout architecture directly into view panels
            viewport.innerHTML = `
                <div class="state-banner">
                    <h2 class="state-title" style="color:#FFF;">${name}</h2>
                    <div class="country-indicator" style="color:${colorHexValue(name)};">${data.country}</div>
                </div>

                <div class="tab-bar">
                    <button class="tab-btn active-tab" onclick="toggleDashboardPane(event, 'pane-finance')">Financials & Intakes</button>
                    <button class="tab-btn" onclick="toggleDashboardPane(event, 'pane-uni')">Flagship Inst.</button>
                    <button class="tab-btn" onclick="toggleDashboardPane(event, 'pane-visa')">Immigration Core</button>
                </div>

                <!-- Pane 1: Financial Analytics & Cost Gauges -->
                <div id="pane-finance" class="tab-content-pane active-pane">
                    <div class="metric-progress-wrapper">
                        <div class="metric-label-row">
                            <span>Tuition Fee Density</span>
                            <span>Scale Index</span>
                        </div>
                        <div class="progress-track">
                            <div class="progress-fill" style="background:${colorHexValue(name)}; width:${data.tuitionIndex}%;"></div>
                        </div>
                        <p style="font-size:0.88rem; margin:6px 0 0 0; color:var(--text-muted);">${data.tuitionText}</p>
                    </div>

                    <div class="metric-progress-wrapper">
                        <div class="metric-label-row">
                            <span>Living Budget Index</span>
                            <span>Scale Index</span>
                        </div>
                        <div class="progress-track">
                            <div class="progress-fill" style="background:${colorHexValue(name)}; width:${data.livingIndex}%;"></div>
                        </div>
                        <p style="font-size:0.88rem; margin:6px 0 0 0; color:var(--text-muted);">${data.livingText}</p>
                    </div>

                    <div style="margin-top:20px;">
                        ${factorsHtml}
                    </div>
                </div>

                <!-- Pane 2: High-Fidelity University Profiles -->
                <div id="pane-uni" class="tab-content-pane">
                    ${uniCards}
                </div>

                <!-- Pane 3: Immigration Pathways & Routes -->
                <div id="pane-visa" class="tab-content-pane">
                    <div class="premium-card" style="color:#10B981;">
                        <div class="card-tag" style="color:#10B981;">Immigration Matrix</div>
                        <h4 style="color:#FFF; margin:0 0 6px 0;">Student Visa Clearance Pathway</h4>
                        <p style="margin:0; font-size:0.9rem; color:var(--text-muted); line-height:1.5;">${data.visaRoute}</p>
                    </div>
                </div>
            `;
        }

        // Functional color mapping helper algorithm
        function colorHexValue(stateName) {
            if (stateName === 'California') return '#3B82F6';
            if (stateName === 'Ontario') return '#EF4444';
            if (stateName === 'Greater London') return '#A855F7';
            if (stateName === 'New South Wales') return '#10B981';
            return '#F59E0B';
        }

        // Functional scope tab switcher algorithm inside panels
        function toggleDashboardPane(event, targetId) {
            document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active-tab'));
            document.querySelectorAll('.tab-content-pane').forEach(p => p.classList.remove('active-pane'));

            event.currentTarget.classList.add('active-tab');
            document.getElementById(targetId).classList.add('active-pane');
        }

        function bindActionsToFeatures(feature, layer) {
            const country = feature.properties.admin;
            if (eliteStudyNations.includes(country)) {
                layer.on({
                    mouseover: targetRegionHover,
                    mouseout: targetRegionOut,
                    click: targetRegionClick
                });

                layer.bindTooltip(`${feature.properties.name}, ${feature.properties.orders || country}`, {
                    permanent: false,
                    direction: "center",
                    className: "neon-map-label"
                });
            }
        }

        // 6. Connect High-Fidelity Global Admin-1 Subnational Boundaries Dataset CDN
        let cyberBoundaryLayer;
        const subnationalCdnUrl = "https://raw.githubusercontent.com/datasets/geo-ne-admin1/master/data/admin1.geojson";

        $.getJSON(subnationalCdnUrl, function(data) {
            cyberBoundaryLayer = L.geoJson(data, {
                style: designVectorLayout,
                onEachFeature: bindActionsToFeatures
            }).addTo(map);
        }).fail(function() {
            console.error("Vector streaming connection lost. Reset dashboard components.");
        });
    </script>
</body>
</html>
