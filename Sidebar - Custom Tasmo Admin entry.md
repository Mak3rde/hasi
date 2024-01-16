
# Step 1: 
open your homassistant configuration.yaml
and add this to it. [^1] [^2] [^3]

>[!NOTE]
>if you allready have a *panel_custom:*  
>entry in you configuration.yaml  
>don't add the *panel_custom:* line again.

```
##Tasmo Admin Aplication Pannel  
panel_custom:
      # Required: The panel_custom integration allows you to write your own panels in JavaScript and add them to Home Assistant. 

  - name: Tasmo Admin
      #Required: Name of the web integration that renders your panel

    sidebar_title: Tasmo Admin  
      # Required: panel title in the sidebar, Omitting means no sidebar entry (but still accessible through the URL) 

    sidebar_icon: mdi:alpha-t-box 
      # Optional: defines the icon used in the side bar, full list -> https://pictogrammers.com/library/mdi/

    url_path: tasmoadmin 
      # Optional: defines the url that will open the entry directly e.g. http://homeassistant.local:9541/

    module_url: /local/tasmo_admin.js 
      # Required: JavaScript path. loads a JavaScript instead of a script.

    embed_iframe: true 
      # Required: The Unifiy Netowrk Application prevents loading it in a iframe so this needs to be set to : false

    require_admin: true 
      # Optional : If admin access is required to see this panel set to : true, if not set to : false.
```      

# Step 2: 
- Preparations
 

>[!NOTE]
>if you want to switch from one to another 
>ensure that you clean your browser cache,
>if you don't, you won't see any changes.

  

 1.  #### Use hard refresh shortcut to Reload and override cache. [^4] [^5] 

    - Chromium based browsers: Shift + F5 or Ctrl + Shift + r
    - Firefox Browser: Ctrl + F5 or Ctrl + Shift + R 


or

 2.  #### Press F12 to Open the developer tools to disable caching. [^4] [^5]

    if you dont have F buttons use this shortcuts instead
    - Windows/Linux - Ctrl + Shift + I 
    - macOS - Cmd + Opt + I 

when the developer tools pannel has opened

- Click the settings button (near the top right).
- Scroll down to the Advanced settings on the bottom right.
- Check the option "Disable Cache (when toolbox is open)".
- Refresh the page. 

>[!CAUTION]
>If the AMD Software Adrenalin Edition is installed,  
>the AMD Software seems to override the browser shortcuts,  
>so the browser developer tools will not open.  
>Instead the shortcut triggers a screenshot capture,  
>to prevent this use F12 to open the developer tools.  
>Or disable or change the shortcut in AMD Adrenalin. 


>This information is as of January 16, 2024.  
>It is possible that the key combinations will change again in the future.  
>Recently the AMD screenshot capture shortcut was Ctrl+Shift+E.  


# Step 3:

- Create a new file  tasmo_admin.js in /homeassistant/www/  
- paste the code block in to your tasmo_admin.js  
- Save the file  
- Restart Homeassistant so it can take effekt.


Use window.replace to open a new window in this case in to a iframe and then set the desired URL

```
window.location.replace("https://<url to Tasmo Admin>");
```



Source:
[^1]: [Concepts and terminology](https://www.home-assistant.io/getting-started/concepts-terminology/)  
[^2]: [panel_custom integration Configuration Variables](https://www.home-assistant.io/integrations/panel_custom/)  
[^3]: [instructions how to build your own panels](https://developers.home-assistant.io/docs/frontend/custom-ui/creating-custom-panels)
[^4]: [Common keyboard shortcuts in Google Chrome](https://support.google.com/chrome/answer/157179)  
[^5]: [Common keyboard shortcuts in Mozilla Firefox](https://support.mozilla.org/en-US/kb/keyboard-shortcuts-perform-firefox-tasks-quickly)  
[^5]: [all keyboard shortcuts used by the developer tools built into Firefox](https://firefox-source-docs.mozilla.org/devtools-user/keyboard_shortcuts/index.html)
