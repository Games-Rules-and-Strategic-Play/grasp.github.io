# Lab Research & Publications

The Games, Rules, and Strategic Play (GRASP) Lab focuses on the intersection of structural graph theory, combinatorial game theory, and discrete mathematics. Below is the automated index of our research publications.

---

\full_bibliography

<!-- Dynamic post-processor script optimized for fallback list structures -->
<script>
document.addEventListener("DOMContentLoaded", function() {
    // Locate all compiled list-item footnotes
    const entries = document.querySelectorAll('li[id^="fn:"]');
    
    entries.forEach(entry => {
        // Target the inner paragraph container
        const targetElement = entry.querySelector('p') || entry;
        const rawHTML = targetElement.innerHTML;
        const rawText = targetElement.innerText;
        
        // Defensive defaults
        let shortAuthor = "Research Paper";
        let titleStr = "View Full Details";
        let yearStr = "";
        
        // 1. Parse fields using standard academic punctuation breaks (". ")
        const parts = rawText.split('. ');
        if (parts.length >= 2) {
            const authorsBlock = parts[0].trim();
            titleStr = parts[1].trim();
            
            // Isolate the primary author's surname
            const firstAuthorRaw = authorsBlock.split(/,|\s+and\s+/)[0].trim();
            const cleanLastName = firstAuthorRaw.replace(/[\.,&]/g, "");
            
            // Check if there are multiple contributors
            const hasMultiple = authorsBlock.includes(',') || authorsBlock.toLowerCase().includes(' and ');
            shortAuthor = hasMultiple ? `${cleanLastName} et al.` : cleanLastName;
        }
        
        // 2. Extract 4-digit publication year from raw text strings
        const yearMatch = rawText.match(/\b(19|20)\d{2}\b/);
        if (yearMatch) {
            yearStr = ` (${yearMatch[0]})`;
        }
        
        // Clean stray footnote backref characters out of visible title field
        titleStr = titleStr.replace(/↩/g, "").trim();
        
        // 3. Inject interactive accordions directly into layout container
        targetElement.innerHTML = `
            <div class="bib-toggle-header" onclick="const details = this.nextElementSibling; const isOpen = details.style.display === 'block'; details.style.display = isOpen ? 'none' : 'block'; this.querySelector('.bib-badge').innerText = isOpen ? 'SHOW MORE ▼' : 'SHOW LESS ▲';">
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