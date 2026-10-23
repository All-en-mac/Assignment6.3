HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Overflow & Layout Fixing</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <!-- Header Section -->
    <header>
        <h1>CSS Overflow Demonstration</h1>
        <p>Exploring visible, hidden, scroll, and auto properties in fixed-height containers.</p>
    </header>

    <main class="container">

        <!-- 1. Overflow: Visible -->
        <section class="overflow-demo">
            <h2>1. overflow: visible (Default)</h2>
            <div class="box visible-box">
                <p>This container has a fixed height, but the text inside is extremely long. Because the overflow property is set to visible, the excess content spills out of the box boundaries and overlaps with whatever elements are positioned below it, causing layout bugs.</p>
            </div>
        </section>

        <!-- 2. Overflow: Hidden -->
        <section class="overflow-demo">
            <h2>2. overflow: hidden</h2>
            <div class="box hidden-box">
                <p>This container has a fixed height. Any content that exceeds these exact dimensions is clipped and hidden entirely from view. The user has no way to scroll or read the overflowing text.</p>
            </div>
        </section>

        <!-- 3. Overflow: Scroll -->
        <section class="overflow-demo">
            <h2>3. overflow: scroll</h2>
            <div class="box scroll-box">
                <p>This container has a fixed height with overflow set to scroll. Horizontal and/or vertical scrollbars are permanently rendered on the box border, allowing users to scroll through the hidden text regardless of whether the content actually overflows.</p>
            </div>
        </section>

        <!-- 4. Overflow: Auto (Recommended) -->
        <section class="overflow-demo">
            <h2>4. overflow: auto (Recommended)</h2>
            <div class="box auto-box">
                <p>This container uses <code>overflow: auto</code>. Scrollbars appear dynamically *only* when the text exceeds the fixed height of the container. If the text fits, no scrollbars are shown, keeping the user interface clean and accessible.</p>
            </div>
        </section>

        <!-- 5. Fixed Layout Bug Example -->
        <section class="overflow-demo">
            <h2>5. Fixing a Real Layout Overflow Issue</h2>
            <div class="broken-layout-fix">
                <p><strong>Fixed Card:</strong> This card previously suffered from text and image overflow due to rigid bounding constraints. By combining <code>max-width</code>, <code>word-break</code>, and <code>overflow: auto</code>, the layout remains fully responsive and neat.</p>
            </div>
        </section>

    </main>

    <footer>
        <p>&copy; 2026 Web Development Practice</p>
    </footer>

</body>
</html>


CSS
/* Global Reset */
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f4f6f9;
    color: #333333;
    line-height: 1.6;
    padding: 20px;
}

header {
    text-align: center;
    margin-bottom: 30px;
}

.container {
    max-width: 700px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 25px;
}

.overflow-demo {
    background-color: #ffffff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.04);
}

.overflow-demo h2 {
    font-size: 1.1rem;
    color: #1e293b;
    margin-bottom: 10px;
}

/* Base Fixed-Height Box Styling for Testing */
.box {
    width: 100%;
    height: 90px; /* Fixed height requirement */
    padding: 12px;
    background-color: #f8fafc;
    border: 2px solid #cbd5e1;
    border-radius: 6px;
    font-size: 0.95rem;
}

/* ==========================================
   OVERFLOW VALUE STYLES
   ========================================== */

/* 1. Visible */
.visible-box {
    overflow: visible; /* Content spills outside */
    border-color: #ef4444;
}

/* 2. Hidden */
.hidden-box {
    overflow: hidden; /* Excess content is clipped */
    border-color: #f59e0b;
}

/* 3. Scroll */
.scroll-box {
    overflow: scroll; /* Scrollbars always present */
    border-color: #3b82f6;
}

/* 4. Auto */
.auto-box {
    overflow: auto; /* Scrollbars appear dynamically when needed */
    border-color: #10b981;
}

/* 5. Fixed Layout Bug Example */
.broken-layout-fix {
    width: 100%;
    max-height: 120px;
    overflow: auto; /* Fixes overflow bug safely */
    padding: 15px;
    background-color: #f0fdf4;
    border: 2px solid #22c55e;
    border-radius: 6px;
}

footer {
    text-align: center;
    margin-top: 40px;
    color: #64748b;
    font-size: 0.9rem;
}