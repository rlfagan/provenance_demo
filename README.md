# 🚦 SCANOSS Provenance Summary GitHub Action

This repository contains a **GitHub Actions** workflow that automates the **provenance analysis** of open-source software components using the **SCANOSS API**. The workflow generates a detailed **report** of **geographic contributions** to the codebase, highlighting contributions from **unsanctioned GEO locations** based on a configurable **watchlist**.

---

## 🧠 **Why Is This Important?**

1. **Supply Chain Security:** Understanding the geographic origin of code contributions helps identify potential **supply chain risks**.
2. **Compliance and Governance:** The workflow flags contributions from **sanctioned countries**, ensuring compliance with:
   - **U.S. Department of the Treasury's OFAC Sanctions**
   - **Export Administration Regulations (EAR)**
   - **International Traffic in Arms Regulations (ITAR)**
3. **M&A Due Diligence:** Provides insights into the **provenance of code**, which is critical during **mergers and acquisitions** to avoid hidden risks.
4. **Open-Source Transparency:** Promotes **trust** and **accountability** by disclosing the **geographic diversity** of the contributor base.

---

## ⚙️ **How It Works**

1. **Provenance API Call:** The workflow uses **curl** to query the **SCANOSS API** for geographic data on code contributions.
2. **GEO Location Analysis:** Extracts **contributor locations** and counts **frequency** using **jq** and **bash**.
3. **Compare Against Sanctions List:** 
   - Loads the **unsanctioned.txt** file from the repository.
   - Marks contributions from **sanctioned countries** with a **🚫 Unsanctioned** status.
4. **Generate Markdown Report:** Creates a **pretty, dynamic report** displayed directly in the **GitHub Actions Job Summary**.
5. **Store Artifacts:** Saves the **raw JSON data**, **provenance summary**, and **markdown report** as downloadable **artifacts**.

---

## 📊 **Example Report Output**

```markdown
# 📄 Provenance Summary for pkg:github/heimdal/heimdal

## 🌍 **Geographic Distribution of Contributors:**
---

| 🌐 **Location**       | 🔢 **Count** | 🛡️ **Status** |
|-----------------------|--------------|---------------|
| California, USA      | 3            | ✅ Allowed    |
| Melbourne, Australia | 3            | ✅ Allowed    |
| Moscow, Russia       | 2            | 🚫 Unsanctioned |
| Tehran, Iran         | 1            | 🚫 Unsanctioned |
| Berlin, Germany      | 1            | ✅ Allowed    |
| Beijing, China       | 1            | 🚫 Unsanctioned |
| New York, NY         | 1            | ✅ Allowed    |

---

## ✅ **Key Takeaways:**
> - 🌐 **Global Reach:** The package has a contributor base from multiple countries, showcasing open-source diversity.  
> - 🚀 **Tech Hubs:** Strong representation from tech hubs like **California**, **Berlin**, **Melbourne**, and **Hyderabad**.  
> - 🚫 **Warning:** Code contributions from **unsanctioned GEO locations** detected!  
