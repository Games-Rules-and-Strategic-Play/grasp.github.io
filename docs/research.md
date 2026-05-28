# Lab Research & Publications

The Games, Rules, and Strategic Play (GRASP) Lab focuses on the intersection of structural graph theory, combinatorial game theory, and discrete mathematics. Below is the automated index of our research publications.

---

\full_bibliography

<!-- Dynamic post-processor script to style entries as expandable short-author elements -->
<script>
document.addEventListener("DOMContentLoaded", function() {
    // Locate all compiled bibtex items
    const entries = document.querySelectorAll(".csl-entry");
    
    entries.forEach(entry => {
        const rawHTML = entry.innerHTML;
        const rawText = entry.innerText;
        
        // Defensive default fallbacks
        let shortAuthor = "Research Paper";
        let yearStr = "";
        let titleStr = "View Full Details";
        
        // Regex patterns to isolate Authors, Years (e.g. (2026)), and Titles
        const yearRegex = /\((\d{4})\)/;
        const yearMatch = rawText.match(yearRegex);
        
        if (yearMatch) {
            yearStr = ` ${yearMatch[0]}`;
            const splitParts = rawText.split(yearMatch[0]);
            
            // 1. Process Authors (Left side of the year)
            const authorsBlock = splitParts[0].trim();
            if (authorsBlock) {
                // Get the very first author name segment
                const firstAuthorRaw = authorsBlock.split(/,|\s+and\s+/)[0].trim();
                // Clean up trailing characters or symbols
                const cleanLastName = firstAuthorRaw.replace(/[\.,&]/g, "");
                
                // Determine if we need an "et al." tag
                const totalAuthorsCount = (authorsBlock.match(/,/g) || []).length;
                shortAuthor = totalAuthorsCount > 1 ? `${cleanLastName} et al.` : cleanLastName;
            }
            
            // 2. Process Title (Right side of the year)
            if (splitParts[1]) {
                const cleanRightSide = splitParts[1].trim().replace(/^[\.\s,]+/, "");
                // Grab the sentence up until the first major punctuation stop
                const titleMatch = cleanRightSide.match(/^[^.]+./);
                if (titleMatch) {
                    titleStr = titleMatch[0].trim();
                } else {
                    titleStr = cleanRightSide.substring(0, 60) + "...";
                }
            }
        } else {
            // Fallback truncation if entry format varies wildly
            titleStr = rawText.substring(0, 75) + "...";
        }
        
        // Build the modern UI card structure
        entry.innerHTML = `
            <div class="bib-toggle-header" onclick="this.nextElementSibling.style.display = this.nextElementSibling.style.display === 'block' ? 'none' : 'block'; this.querySelector('.bib-badge').innerText = this.nextElementSibling.style.display === 'block' ? 'SHOW LESS ▲' : 'SHOW MORE ▼';">
                <div class="bib-summary-text">
                    <span style="color: var(--orange);">${shortAuthor}${yearStr}</span> — ${titleStr}
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