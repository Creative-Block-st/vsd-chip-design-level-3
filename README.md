# Introduction
You all have used simple electronic appliances like washing machines, refrigerators, microwaves, ovens etc. and also some smart appliances and other products like laptops and mobiles. Many of the appliances are able to perform one task and some to perform one task more eficiently and some are to perform multiple tasks. But, what is common among all of these products, that is its processing unit, its core. That is its chip! 
Chip design is a very interesting (and comlex) medium in chip design we can create everything that we want for our use and th euse of the world or it can be a way to do so.
# OpenLane
Here we are talking about an open source package desigened to create *GDSII* file while we put input of *RTL* and *PDK* files. These files are very complicated to understand in one view. But we are not here about that all file task. We will just understand about, What comes under OpenLANE Package.<br>
<ol type=1>
<li> Synthesis
<li>Floor planning and Power Planning
<li>Placement
<li>Clock tree synthesis
<li>Routing
<li>Sign off
</ol>
<br>
Before moving directly towards the first step, that is synthesis, we will take a look on the fundamentals which will be influensing in our work. 
<pre id="code-block">
  <code>
    def my_function(x):
      """This is an example function."""
      return x * 2

    print(my_function(5))
  </code>
</pre>

<button id="copy-button">Copy</button>

<script>
  const codeBlock = document.getElementById('code-block');
  const copyButton = document.getElementById('copy-button');

  copyButton.addEventListener('click', () => {
    const range = document.createRange();
    range.selectNodeContents(codeBlock);
    window.getSelection().removeAllRanges();
    window.getSelection().addRange(range);
    navigator.clipboard.writeText(window.getSelection().toString())
      .then(() => {
        copyButton.textContent = 'Copied!';
        setTimeout(() => {
          copyButton.textContent = 'Copy';
        }, 2000); // Reset button text after 2 seconds
      })
      .catch(errf => {
        console.error('Failed to copy: ', err);
        copyButton.textContent = 'Error';
      });
  });
</script> 