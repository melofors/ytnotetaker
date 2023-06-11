//get api key from apikey.js
import { apiKey } from './apikey.mjs'

//clear if already exists
const checkExist = document.getElementById('buttonId');
if(checkExist){
  checkExist.remove();
}

//beginning of program
const checkTargetNode = () => {
  const targetNode = document.getElementsByClassName('style-scope ytd-watch-next-secondary-results-renderer')[2];
  if (targetNode) {
      console.log('Target node found:', targetNode);
      console.log("[content script] is working");

      //create el button
      let element = document.createElement("BUTTON");
      element.id = 'buttonId';
      element.appendChild(document.createTextNode('Generate Notes'));
      document.getElementsByClassName('style-scope ytd-watch-next-secondary-results-renderer')[2].insertBefore(element, document.getElementsByClassName('style-scope yt-related-chip-cloud-renderer')[0]);
      
      //create text element
      let textElement = document.createElement("p");
      textElement.id = 'textId';

      document.getElementById('buttonId').addEventListener('click', async function() {
        const url = 'https://prometheus-api.llm.llc/api/workflow/4CHbGxnTuDJskmHwGgvP';
        const args = 'bro';
        
        fetch(url, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json'
          },
          body: JSON.stringify({
            apiKey,
            args
          })
        })
          .then(response => response.json())
          .then(data => {
            console.log(data.outputs[0]);

            textElement.innerHTML = '';
            textElement.appendChild(document.createTextNode(data.outputs[0]));
            
            textElement.style.color = '#FFFFFF';

            document.getElementsByClassName('style-scope ytd-watch-next-secondary-results-renderer')[2].insertBefore(textElement, document.getElementsByClassName('style-scope yt-related-chip-cloud-renderer')[0]);
      
            // Store the data in a variable or perform any other actions with it
          })
          .catch(error => {
            console.error('Error:', error);
          });
      });
    
    } else {
      console.log('Target node not found, trying again in 100ms');
      setTimeout(checkTargetNode, 100);
  }
    };
  checkTargetNode();
