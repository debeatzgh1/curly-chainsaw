                                                      <!doctype html>




Live Preview Button Changer
<style>
body { font-family: Arial,sans-serif; background:#0a0a0a; color:#fff; display:flex; flex-direction:column; align-items:center; padding:20px; }
h1 { color:#00ff88; text-align:center; margin-bottom:20px; }
textarea, input[type="text"] { width:100%; max-width:800px; padding:10px; margin-bottom:12px; border-radius:8px; border:1px solid #444; background:#111; color:#fff; font-family:monospace; }
.button-config { background:#111; padding:15px; border-radius:10px; margin-bottom:15px; width:100%; max-width:800px; }
.button-config label { display:block; margin-bottom:6px; font-weight:bold; }
.colors { display:flex; gap:12px; margin-bottom:8px; }
.colors label { cursor:pointer; display:flex; align-items:center; gap:6px; }
.colors input[type="radio"] { accent-color:currentColor; }
button.update-btn { padding:10px 20px; background:#00ff88; border:none; border-radius:8px; cursor:pointer; font-weight:bold; color:#000; margin-bottom:12px; transition:transform .1s; }
button.update-btn:hover { transform:scale(1.05); }
pre#output { width:100%; max-width:800px; background:#111; padding:12px; border-radius:8px; border:1px solid #444; white-space:pre-wrap; overflow-wrap:break-word; cursor:pointer; }
#preview { display:flex; gap:12px; flex-wrap:wrap; justify-content:center; margin-top:12px; padding:12px; background:#111; border-radius:8px; width:100%; max-width:800px; border:1px solid #444; }
#preview a { padding:10px 20px; border-radius:8px; color:#000; text-decoration:none; font-weight:bold; }
</style>



<h1>Live Preview Button Changer</h1>

<label for="htmlInput">Paste your HTML code here:</label>
<textarea id="htmlInput" placeholder="Paste your HTML code with 3 buttons here..."></textarea>

<!-- Button Configs -->
<div class="button-config" data-btn="1">
  <label>Button 1 URL:</label>
  <input type="text" class="urlInput" placeholder="https://example.com/1" />
  <div class="colors">
    <label><input type="radio" name="color1" value="red" /> Red</label>
    <label><input type="radio" name="color1" value="yellow" /> Yellow</label>
    <label><input type="radio" name="color1" value="green" checked /> Green</label>
  </div>
</div>

<div class="button-config" data-btn="2">
  <label>Button 2 URL:</label>
  <input type="text" class="urlInput" placeholder="https://example.com/2" />
  <div class="colors">
    <label><input type="radio" name="color2" value="red" /> Red</label>
    <label><input type="radio" name="color2" value="yellow" /> Yellow</label>
    <label><input type="radio" name="color2" value="green" checked /> Green</label>
  </div>
</div>

<div class="button-config" data-btn="3">
  <label>Button 3 URL:</label>
  <input type="text" class="urlInput" placeholder="https://example.com/3" />
  <div class="colors">
    <label><input type="radio" name="color3" value="red" /> Red</label>
    <label><input type="radio" name="color3" value="yellow" /> Yellow</label>
    <label><input type="radio" name="color3" value="green" checked /> Green</label>
  </div>
</div>

<button class="update-btn" id="updateBtn">Update HTML Script</button>

<h3>Live Preview:</h3>
<div id="preview">
  <a href="#" target="_blank" id="previewBtn1">Button 1</a>
  <a href="#" target="_blank" id="previewBtn2">Button 2</a>
  <a href="#" target="_blank" id="previewBtn3">Button 3</a>
</div>

<h3>Updated HTML Script:</h3>
<pre id="output">Click "Update HTML Script" to generate code here. Click box to copy.</pre>

<script>
const htmlInput = document.getElementById('htmlInput');
const updateBtn = document.getElementById('updateBtn');
const output = document.getElementById('output');

const previewBtn1 = document.getElementById('previewBtn1');
const previewBtn2 = document.getElementById('previewBtn2');
const previewBtn3 = document.getElementById('previewBtn3');

function updatePreviewAndHTML(){
  let html = htmlInput.value;

  for(let i=1;i<=3;i++){
    const btnConfig = document.querySelector(`.button-config[data-btn="${i}"]`);
    const url = btnConfig.querySelector('.urlInput').value.trim() || '#';
    const color = btnConfig.querySelector(`input[name="color${i}"]:checked`).value;

    // Update live preview buttons
    const previewBtn = document.getElementById(`previewBtn${i}`);
    previewBtn.href = url;
    previewBtn.style.background = color;

    // Replace URLs in HTML
    const regexUrl = new RegExp(`(href|src)=(["'])(.*?button${i}.*?)\\2`, 'gi');
    html = html.replace(regexUrl, `$1="$2${url}$2`);

    // Replace inline background colors in HTML
    const regexColor = new RegExp(`(button\\s*\\#?button${i}.*?)(background\\s*:\\s*.*?;?)`,'gi');
    html = html.replace(regexColor, `$1background:${color};`);

    // Replace color class names if any
    const regexClass = new RegExp(`(class\\s*=\\s*["'][^"']*button${i}-)(red|yellow|green)([^"']*["'])`, 'gi');
    html = html.replace(regexClass, `$1${color}$3`);
  }

  output.textContent = html;
}

updateBtn.addEventListener('click', updatePreviewAndHTML);

// Copy output on click
output.addEventListener('click', () => {
  navigator.clipboard.writeText(output.textContent).then(()=>alert('Updated HTML copied to clipboard!'));
});
</script>


</!doctype>                                                                                                                                                   | Project                                                                                                                                                      | Description                                                                                                         | Action                                                                                                           |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| ![Custom Blogger Theme](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/generateamobile-firstresponsivebloggertemplatewithcustomizablecolorsfontsandsections1576324612066211977.jpg)                                                            | **[Custom Blogger Theme with Dynamic Post Loading and Logo](https://debeatzgh1.github.io/Custom-Blogger-Theme-for-with-Dynamic-Post-Loading-and-Logo-/)**    | A responsive, mobile-first Blogger theme with customizable sections, dynamic post loading, and custom logo support. | [🔗 View Demo](https://debeatzgh1.github.io/Custom-Blogger-Theme-for-with-Dynamic-Post-Loading-and-Logo-/)       |
| ![Popup Generator](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createatoolthatgeneratesiframeorcard-styleembedsforindividualbloggerpostscompletewiththumbnailtitleandreadmorebuttonforcross-blogpromotion754077096311972631.jpg)            | **[Popup HTML Page Generator](https://debeatzgh1.github.io/popup-html-page-generator-blogger/)**                                                             | Easily generate iframe or card-style embeds for individual Blogger posts with thumbnails and read-more buttons.     | [🔗 View Demo](https://debeatzgh1.github.io/popup-html-page-generator-blogger/)                                  |
| ![Newsletter Widget](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernflat-styleillustrationofanotificationbellwithglowinghighlightssurroundedbyabstractshapespaperenvelopesanddigitalicons28emailmessageupdate293314991682681990671.jpg) | **[Sliding Newsletter Signup Widget](https://debeatzgh1.github.io/Sliding-Newsletter-Signup-Widget-with-Pulse-Animation/)**                                  | A modern newsletter signup widget with sliding animation and pulsing notification highlights.                       | [🔗 View Demo](https://debeatzgh1.github.io/Sliding-Newsletter-Signup-Widget-with-Pulse-Animation/)              |
| ![Product Carousel](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designacleanmodernthumbnailforabloggerproductscarouseltool1711994558720457535.jpg)                                                                                          | **[Blogger Product Carousel with WhatsApp Floating Button](https://debeatzgh1.github.io/Blogger-Product-Carousel-with-WhatsApp-Floating-Button/)**           | Showcase Blogger products in a responsive carousel with a built-in WhatsApp floating button for instant contact.    | [🔗 View Demo](https://debeatzgh1.github.io/Blogger-Product-Carousel-with-WhatsApp-Floating-Button/)             |
| ![Floating Dock](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernminimallayoutwithafloatingdockofcolorfulroundicons28patreonbloggergithub29ontherightsideofacleanwebpagemockup6676994054500999142.jpg)                                   | **[Floating Dock Smart Iframe Modal](https://debeatzgh1.github.io/-Floating-Dock-Smart-Iframe-Modal/)**                                                      | A modern floating dock with colorful round icons and iframe modal integration.                                      | [🔗 View Demo](https://debeatzgh1.github.io/-Floating-Dock-Smart-Iframe-Modal/)                                  |
| ![Tailwind Homepage](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamodernandcleanthumbnailforawebdevelopmentproducttitledmodernhomepagestylingtemplatewithtailwindcss3420170625469385526.jpg)                                          | **[Modern Homepage Styling with TailwindCSS](https://debeatzgh1.github.io/Modern-homepage-styling-with-TailwindCSS-/)**                                      | A clean and modern homepage layout template styled with TailwindCSS.                                                | [🔗 View Demo](https://debeatzgh1.github.io/Modern-homepage-styling-with-TailwindCSS-/)                          |
| ![TechAdapt Solutions](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/wp-17550417188267308669484942620808.jpg)                                                                                                                                 | **[TechAdapt Solutions – Strategies for Modern Startups](https://debeatzgh1.github.io/TechAdapt-Solutions-Strategies-for-Modern-Startups-and-Individuals/)** | Practical strategies, resources, and tools for startups and individuals adapting to the modern digital world.       | [🔗 View Demo](https://debeatzgh1.github.io/TechAdapt-Solutions-Strategies-for-Modern-Startups-and-Individuals/) |

---

## 🛠️ Features

* ✅ Fully responsive designs
* ✅ Blogger-friendly & easy to embed
* ✅ Lightweight, no heavy dependencies
* ✅ Includes floating buttons, modals, and animations
* ✅ Perfect for enhancing engagement & monetization

---

## 📌 Explore More Scripts

👉 Check out the full curated collection here:
[**Firebase Curated Front-End Components**](https://github.com/debeatzgh1/firebase-front-end-components)

---

## 💡 Contribution

Want to suggest improvements or add your own scripts?

* Open an **issue**
* Submit a **pull request**
* Share your ideas in the discussions

---

## 📜 License

This project is released under the **MIT License** – free to use, modify, and share with attribution.

---

✨ Designed for creators, bloggers, and developers who want to level up their Blogger sites with modern UI components.

---


# 🌐 Personal Portfolio Website

A simple and responsive personal portfolio website built with **HTML, CSS, and JavaScript**.  
This project is perfect for showcasing your skills, projects, and contact information.  

Live Demo 👉 [View Portfolio](https://debeatzgh.github.io/portfolio-site/)

---

## ✨ Features
- Responsive design (works on mobile & desktop)  
- Navigation bar with smooth scrolling  
- Hero section with intro & call-to-action button  
- About section with bio details  
- Projects section with cards  
- Contact section with email & social links  
- **Dark mode toggle** 🌙☀️  

---

## 🛠️ Technologies Used
- **HTML5** – Structure  
- **CSS3** – Styling & Responsive design  
- **JavaScript (Vanilla)** – Interactivity (dark mode toggle)  
- **GitHub Pages** – Free hosting & deployment  

---

## 🚀 Getting Started
To run this project locally:  

1. Clone the repository:
   ```bash
   git clone https://github.com/debeatzgh1/portfolio-site.git

# 🚀 DeBeatzGH – AI Tools & Side Hustle Hub  

![DeBeatzGH Thumbnail](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticdesignfeaturinganai-themedicon28likeabraincircuitorrobot29overlaidwithdebeatzghoraitoolshustles6089986211026037047.jpg)  

## 🌟 About  
Welcome to **[DeBeatzGH](https://debeatzgh.wordpress.com/)** — your go-to hub for **AI tools, side hustle strategies, blogging resources, and digital growth guides**.  

Our platform is built to help **students, creators, startups, and professionals** unlock the power of AI, monetize their skills, and thrive in today’s digital economy.  

### ✨ What You’ll Find  
- 💡 Explore **AI prompts, tools, and hacks**  
- 📈 Discover **side hustle strategies & online income ideas**  
- ✍️ Access **blogging & digital business guides**  
- 🚀 Stay ahead with **regular updates and fresh insights**  

---

## 👉 Get Started  
🔥 **Start your journey today → [Visit DeBeatzGH]([https://debeatzgh.wordpress.com/](https://www.patreon.com/debeatzgh/collections))**  

---


<!-- README: DebeatzGH Digital Store (HTML-friendly for GitHub) -->
<div align="center">
  <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener">
    <img
      src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg"
      alt="DebeatzGH Digital Store"
      style="max-width:100%; border-radius:16px;"
    />
  </a>

  <h1 style="margin-top: 14px;">DebeatzGH Digital Store</h1>
  <p style="max-width:780px;">
    Your hub for AI insights, tech tutorials, side-hustle playbooks, and productivity tools.
    Learn, build, and launch digital projects faster.
  </p>

  <!-- CTAs -->
  <p>
    <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin:4px; border-radius:999px; text-decoration:none; font-weight:600; border:1px solid #2563eb;">
      🚀 View Live App
    </a>
    <a href="https://github.com/debeatzgh1/Personal-Portfolio-site-" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin:4px; border-radius:999px; text-decoration:none; font-weight:600; border:1px solid #111827;">
      ⭐ Star this Repo
    </a>
  </p>
</div>

<hr/>

<h2>Overview</h2>
<p>
  <strong>DebeatzGH</strong> helps beginners and creators build profitable digital assets:
  blogs, affiliate funnels, AI-assisted content, and more. Explore tutorials, tools, and
  ready-to-use components to speed up your workflow.
</p>

<h2>Features</h2>
<ul>
  <li><strong>AI & Tech Learning:</strong> Bite-sized guides for modern tools and workflows.</li>
  <li><strong>Side-Hustle Playbooks:</strong> Practical steps to validate and launch ideas.</li>
  <li><strong>Productivity Toolkit:</strong> Reusable widgets, templates, and scripts.</li>
  <li><strong>Beginner-Friendly:</strong> Clear explanations, curated resources, and examples.</li>
</ul>

<h2>Quick Start</h2>
<ol>
  <li>Clone:
    <pre><code>git clone https://github.com/debeatzgh1/Personal-Portfolio-site-</code></pre>
  </li>
  <li>Enter folder:
    <pre><code>cd debeatzgh</code></pre>
  </li>
  <li>Install deps (adjust to your stack):
    <pre><code># Node
npm install
npm run dev

# or Python
pip install -r requirements.txt
python app.py</code></pre>
  </li>
  <li>Open in browser:
    <pre><code>http://localhost:3000</code></pre>
  </li>
</ol>

<h2>Project Links</h2>
<ul>
  <li>🌐 Live App: <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener">socialcreator.com/debeatzgh</a></li>
  <li>🖼️ Thumbnail: <a href="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg" target="_blank" rel="noopener">View image</a></li>
</ul>

<h2>Contributing</h2>
<p>
  Contributions are welcome! Open an issue for bugs or ideas. For changes, fork the repo,
  create a feature branch, and submit a pull request.
</p>

<h2>License</h2>
<p>
  Released under the <a href="./LICENSE">MIT License</a>.
</p>

<hr/>

<div align="center">
  <p><em>If this project helps you, consider giving it a star. It really helps! ⭐</em></p>
  <p>
    <a href="https://www.socialcreator.com/debeatzgh/?s=314768" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin-top:6px; border-radius:10px; text-decoration:none; font-weight:600; border:1px solid #2563eb;">
      PRODUCTS →
    </a>
  </p>
</div>
