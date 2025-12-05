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


</!doctype>
