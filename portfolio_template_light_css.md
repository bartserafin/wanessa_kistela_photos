/* Root variables store the color palette, typefaces, and reusable theme values used throughout the page. */
:root {
    --bg-color: #fafafa;
    --text-color: #2b2b2b;
    --accent-color: #d7c38e; /* Bright green accent */
    --card-bg: #ffffff;
    --font-heading: 'Playfair Display', serif;
    --font-body: 'Inter', sans-serif;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
    overflow-x: hidden;
}

body {
    background-color: var(--bg-color);
    color: var(--text-color);
    font-family: var(--font-body);
    line-height: 1.7;
    overflow-x: hidden;
}

/* Navigation bar styles: controls the top fixed menu container, transparency, and layout of the nav links. */
nav {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    padding: 18px 5vw;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 24px;
    background: rgba(46, 45, 45, 0.63);
    z-index: 1000;
    backdrop-filter: blur(18px);
    border: none;
    border-radius: 0;
    box-shadow: 20px 20px 60px rgba(0, 0, 0, 0.1);
}

nav .logo {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.5rem;
    font-weight: 500;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--accent-color);
}

nav .links {
    display: flex;
    align-items: center;
    gap: 50px;
    flex-wrap: wrap;
    justify-content: center;
}

nav .links a {
    font-family: 'Montserrat', sans-serif;
    color: rgba(255,255,255,0.92);
    text-decoration: none;
    font-weight: 500;
    font-size: 0.95rem;
    text-transform: uppercase;
    letter-spacing: 0.25em;
    position: relative;
    transition: color 0.25s ease;
}

nav .links a:hover {
    color: #d7c38e;
}

nav .links a::after {
    content: '';
    position: absolute;
    width: 0;
    height: 2px;
    bottom: -5px;
    left: 0;
    background-color: #d7c38e;
    transition: width 0.3s ease;
}

nav .links a:hover::after {
    width: 100%;
}

/* Typography defaults for headings. These rules set the font family and base color for page headings. */
h1, h2, h3 {
    font-family: var(--font-heading);
    font-weight: 400;
    color: #111;
}

h2 {
    font-size: 3rem;
    text-align: center;
    margin-bottom: 40px;
}

/* Standard section spacing: applies consistent padding and minimum height for each main content section. */
section {
    padding: 120px 5vw;
    min-height: 100vh;
}

/* Hero section styling: positions the slider background and places the hero content at the bottom. */
/* Hero Full-width Slider */
#home {
    padding: 0px;
    height: auto;
    position: relative;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    padding-bottom: 0px;
    overflow: hidden;
    width: 100vw;
}

.slider-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    overflow: hidden;
}

.slide {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
    opacity: 0;
    transform: translateX(100%);
    transition: transform 0.5s ease-in-out, opacity 0.5s ease-in-out;
}

.slide.active {
    opacity: 1;
    transform: translateX(0);
}

/* Exit animations for current slide */
.slide.exit-left {
    animation: slideOutLeft 0.5s ease-in-out forwards;
}

.slide.exit-right {
    animation: slideOutRight 0.5s ease-in-out forwards;
}

/* Enter animations for incoming slide */
.slide.enter-from-right {
    animation: slideInFromRight 0.5s ease-in-out forwards;
}

.slide.enter-from-left {
    animation: slideInFromLeft 0.5s ease-in-out forwards;
}

@keyframes slideOutLeft {
    to {
        opacity: 0;
        transform: translateX(-100%);
    }
}

@keyframes slideOutRight {
    to {
        opacity: 0;
        transform: translateX(100%);
    }
}

@keyframes slideInFromRight {
    from {
        opacity: 0;
        transform: translateX(100%);
    }
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

@keyframes slideInFromLeft {
    from {
        opacity: 0;
        transform: translateX(-100%);
    }
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

.slide::after {
    content: '';
    position: absolute;
    inset: 0;
    background: rgba(250, 250, 250, 0.3); /* Light overlay to make text readable */
}

/* Slider arrow buttons for manual navigation */
.slider-arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(255, 255, 255, 0.3);
    border: 2px solid rgba(255, 255, 255, 0.6);
    color: #fff;
    font-size: 2rem;
    width: 50px;
    height: 50px;
    cursor: pointer;
    z-index: 100;
    border-radius: 4px;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
}

.slider-arrow:hover {
    background: rgba(255, 255, 255, 0.5);
    border-color: rgba(255, 255, 255, 0.9);
}

.slider-prev {
    left: 20px;
}

.slider-next {
    right: 20px;
}

.hero-content {
    text-align: center;
    background: rgba(255, 255, 255, 0.85);
    width: 100%;
    padding: 10px;
    border-radius: 4px;
    backdrop-filter: blur(15px);
    border-top: 2px solid var(--accent-color);
}

.hero-content h1 {
    font-size: 2.5rem;
    margin-bottom: 10px;
    font-style: italic;
}

.hero-content p {
    font-size: 1.2rem;
    letter-spacing: 2px;
     margin-bottom: 5px;
    text-transform: uppercase;
    color: #555;
}

/* Portfolio filters and masonry gallery styles: controls the category buttons and the responsive grid of project cards. */
/* Categories & Masonry Portfolio */
.filters {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-bottom: 50px;
    flex-wrap: wrap;
}

.filter-btn {
    background: none;
    border: none;
    font-family: var(--font-body);
    font-size: 1rem;
    color: #777;
    cursor: pointer;
    padding: 5px 10px;
    transition: color 0.3s;
    position: relative;
}

.filter-btn.active, .filter-btn:hover {
    color: var(--text-color);
}

.filter-btn.active::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 20px;
    height: 2px;
    background-color: var(--accent-color);
}

.masonry {
    column-count: 3;
    column-gap: 20px;
}

@media (max-width: 900px) {
    .masonry { column-count: 2; }
}

@media (max-width: 600px) {
    .masonry { column-count: 1; }
}

.masonry-item {
    break-inside: avoid;
    margin-bottom: 20px;
    position: relative;
    overflow: hidden;
    border-radius: 4px;
    cursor: pointer;
    transition: opacity 0.5s ease, transform 0.5s ease;
}

.masonry-item.hidden {
    display: none;
}

.masonry-item img {
    width: 100%;
    display: block;
    transition: transform 0.7s ease;
}

.masonry-item:hover img {
    transform: scale(1.05);
}

.item-overlay {
    position: absolute;
    inset: 0;
    background: rgba(0, 230, 118, 0.85); /* Bright green overlay */
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.4s ease;
}

.masonry-item:hover .item-overlay {
    opacity: 1;
}

.item-overlay h3 {
    color: white;
    font-size: 1.5rem;
    transform: translateY(20px);
    transition: transform 0.4s ease;
}

.masonry-item:hover .item-overlay h3 {
    transform: translateY(0);
}

/* Services / expertise cards: styles the grid container and the individual service cards. */
/* Services & Info Cards */
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 40px;
    max-width: 1200px;
    margin: 0 auto;
}

.card {
    background: var(--card-bg);
    padding: 50px 30px;
    text-align: center;
    box-shadow: 0 10px 30px rgba(0,0,0,0.03);
    border-bottom: 3px solid transparent;
    transition: transform 0.4s ease, border-color 0.4s ease;
}

.card:hover {
    transform: translateY(-10px);
    border-color: var(--accent-color);
}

.card h3 {
    font-size: 1.8rem;
    margin-bottom: 20px;
}

/* Reveal animations: fades content into view when it enters the viewport during scrolling. */
/* Smooth Fade-in Animations */
.reveal {
    opacity: 0;
    transform: translateY(40px);
    transition: all 1s cubic-bezier(0.5, 0, 0, 1);
}

.reveal.active {
    opacity: 1;
    transform: translateY(0);
}

/* About Section */
.about-content {
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
    font-size: 1.1rem;
    color: #555;
}

.about-content p {
    margin-bottom: 20px;
}

/* Testimonials */
.testimonial-block {
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
}

.quote-icon {
    font-family: var(--font-heading);
    font-size: 4rem;
    color: var(--accent-color);
    line-height: 1;
    margin-bottom: -20px;
}

.testimonial-text {
    font-family: var(--font-heading);
    font-size: 1.8rem;
    font-style: italic;
    margin-bottom: 30px;
    color: #333;
}
