# WAFeatureEnabler
Script that enables all AB features in WhatsApp Web.

> [!CAUTION] 
> This JavaScript code is for **research purposes** only and is not intended to be used as a basis for any commercial or non-research purposes.  
> The use of this code is at the user's own risk, and the author(s) assume no responsibility for any misuse or unintended consequences.  
>
> **By using this code, the user acknowledges and agrees to the following:**
> 
> - The user is solely responsible for any legal consequences arising from the use of this code.  
> - The user will not hold the author(s) liable for any damages, losses, or legal actions resulting from the use of this code.  
> - The user agrees to comply with any applicable laws and regulations, including but not limited to copyright, intellectual property, and privacy laws.  
> - Furthermore, the user acknowledges that using this code may violate WhatsApp's Terms of Service and could potentially lead to account bans or other penalties.  
> - The user is advised to consult their own legal counsel before using this code to ensure compliance with all applicable laws and regulations.  
## Usage
1. Open WhatsApp Web in your browser.
2. Press F12 to open the developer tools.
3. Go to the `console` tab.
4. Paste the script.
```js
const features = {};
const orig = require('WAWebABProps').getABPropConfigValue;
console.log("FeatureName\t\t\t\tOriginal Value\t\t\t\tNew Value");

require('WAWebABProps').getABPropConfigValue = f => {
    const ret = orig(f);
    const list = ["is_meta_employee_or_internal_tester","biz_ai_smb_agents_automatic_reply_enabled", "username_contact_display", "username_contact_display", "lists_feature_enabled" ,"files_media_hub_web" ,"animated_race_mercedes_car_emoji_enabled", "custom_racing_emoji_feb2025", "search_the_web_url_offer", "search_the_web_text_search", "username", "ai"];
    const val = (list.some(e => f.includes(e)) && ret === false) ? true : ret;
    if (features[f] === undefined) console.log(`[+] ${f.padEnd(30)} ${String(ret).padEnd(30)} ${val}`);
    features[f] = ret;
    return val;
};

```
