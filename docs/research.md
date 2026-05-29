# Lab Research & Publications

The Games, Rules, and Strategic Play (GRASP) Lab focuses on the intersection of structural graph theory, combinatorial game theory, and discrete mathematics. Below is the automated index of our research publications. 

---

\full_bibliography

<!-- Dynamic text post-processor for Title (Year) arrangement -->
<script>
document.addEventListener("DOMContentLoaded", function() {
    // Selects both CSL entries and standard fallback paragraph outputs
    const entries = document.querySelectorAll(".csl-entry, .bibliography > p, .bibtex-entry");
    
    entries.forEach(entry => {
        const rawHTML = entry.innerHTML;
        const rawText = entry.innerText.trim();
        if (!rawText) return;

        let titleStr = "Untitled Publication";
        let yearStr = "";

        // 1. Isolate the publication year via 4-digit boundaries
        const yearMatch = rawText.match(/\b(19|20)\d{2}\b/);
        if (yearMatch) {
            yearStr = `(${yearMatch[0]})`;
        }

        // 2. Isolate the title via standard sentence punctuation spacing
        const parts = rawText.split(/\.\s+/);
        if (parts.length >= 2) {
            titleStr = parts[1].trim();
            titleStr = titleStr.replace(/\.$/, ""); // Clean hanging periods
        } else {
            titleStr = rawText.split("URL:")[0].substring(0, 80) + "...";
        }

        // Intercept inline trailing block strings safely
        if (titleStr.includes("URL:")) {
            titleStr = titleStr.split("URL:")[0].trim();
        }

        // Restructure target DOM node
        entry.innerHTML = `
            <div class="bib-toggle-header" onclick="
                const drawer = this.nextElementSibling;
                const btn = this.querySelector('.bib-badge');
                if (drawer.style.display === 'block') {
                    drawer.style.display = 'none';
                    btn.innerText = 'SHOW MORE ▼';
                } else {
                    drawer.style.display = 'block';
                    btn.innerText = 'SHOW LESS ▲';
                }
            ">
                <div class="bib-summary-text">
                    ${titleStr} <span class="bib-summary-year">${yearStr}</span>
                </div>
                <button class="bib-badge">SHOW MORE ▼</button>
            </div>
            <div class="bib-expanded-details">
                ${rawHTML}
            </div>
        `;
    });
});
</script>