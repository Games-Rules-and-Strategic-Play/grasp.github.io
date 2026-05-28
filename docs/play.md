<iframe 
    src="https://partitiongames.netlify.app/" 
    style="width: 100vw; height: calc(100vh - 96px); border: none; background: transparent; margin: 0; padding: 0; position: fixed; top: 96px; left: 0;" 
    allowtransparency="true">
</iframe>

<style>
/* Hides the page title heading specifically on this page */
.md-content h1, 
h1 {
    display: none !important;
}

/* Prevents the main site layout from adding default top padding where the title was */
.md-content__inner {
    margin-top: 0 !important;
    padding-top: 0 !important;
}

body, html {
    margin: 0 !important;
    padding: 0 !important;
    height: 100% !important;
    width: 100% !important;
    overflow: hidden; /* Prevents double desktop scrollbars so the game canvas scrolls cleanly */
}

.md-container, .md-main, .md-main__inner, .md-content {
    margin: 0 !important;
    padding: 0 !important;
    height: auto !important;
}

.md-tabs {
    position: relative !important;
    z-index: 10 !important;
    margin: 0 !important;
}
</style>