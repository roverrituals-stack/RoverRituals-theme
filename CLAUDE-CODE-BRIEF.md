# FETCHMATE THEME BRIEF - instructions for Claude Code

You are editing a Shopify theme that has been pulled to this folder.
Target file: `templates/product.fetchmate-2.json`
New file to create: `snippets/faq-fetchmate.liquid`

## RULES

1. This repo syncs to the Shopify theme named `RoverRituals-theme/main`, which is
   a DRAFT theme and is NOT the live store. The live theme is a separate one
   called `RoverRituals 21-8-25` and is not connected to this repo.
   This means you can commit to the `main` branch normally. Changes appear on the
   draft theme within a minute or two and no shopper sees them.
   You must NOT publish the theme, and you must not run `shopify theme push`.
   Publishing is the user's decision after they preview.
2. `templates/product.fetchmate-2.json` is a JSON file with a `/* ... */` comment
   block at the top. Preserve that comment block exactly.
3. After every edit, verify the file is still valid JSON.
4. Do not touch any block, section or setting not named in this brief.
5. Do not reformat or reindent the whole file. Make surgical edits only.
6. Show the user a summary of each change as you go.

## WHY THIS MATTERS

The page currently advertises an "infrared sensor" and "auto-launch every 10
seconds". Neither exists on either version of this product. The manuals confirm
there is no motion or obstacle sensor, and the machine fires once per ball drop
with no timer. These claims must be removed, not softened. The product throws a
ball up to 45 feet and the page implies it can detect obstacles.

## VERIFIED FACTS (from the manufacturer manuals, use these and nothing else)

CLASSIC
- Ball size: 48 to 50mm
- Distances: 10 / 20 / 30 ft, starts at 10 ft when switched on
- Fires about 5 seconds after a ball is dropped in
- Wait for the internal roller to stop before dropping the next ball
- Indicator light: flashing red = ball inside or launching, green = empty
- No motion or obstacle sensor
- Auto standby after about 30 min unused; hold Distance Setting 3 sec to wake
- Cannot be used while charging
- Battery charge/play time: NOT DOCUMENTED. Do not state figures for the Classic.

UPGRADED
- Ball size: 54 to 58mm ETPU (2.13 to 2.28 inches)
- Distances: 19 / 32 / 45 ft, starts at 19 ft when switched on
- Fires with no delay; next ball after about 4 seconds
- Random distance mode: hold Distance Setting 3 sec, throw varies across all three
- Battery: about 5 to 6 hours play, about 6 hours charge at 5V 2A
- No motion or obstacle sensor
- Auto standby after about 30 min unused
- Cannot be used while charging
- Designed for outdoor use; indoors keep it on the 19 ft setting

STYLE: US English. No em-dashes or en-dashes anywhere. Use a hyphen or reword.

---

# TASK 0 - Pre-flight check, do this first

The draft theme in this repo was copied from the live theme at an earlier point,
and the live theme has been edited since. The file here may therefore differ from
what this brief was written against. Confirm before editing anything.

Check that `templates/product.fetchmate-2.json` exists and contains all of these
exact strings:

- `collapsible_tab_UDXTX9`
- `collapsible_tab_GreT7C`
- `rich_text_6mpUN9`
- `multicolumn_nLHK4B`
- `column_EpmRyw`
- `lumin_mega_LjFxmR`
- `custom_columns_wj766j`
- `icon_with_text_naBAkH`
- `comparison_table_pFrHmC`
- `row_P7CGYM`
- `custom_liquid_q73bfX`
- `faq_6HVkFq`
- `collapsible_row_3nw4Nm`
- `Infrared sensor fires the ball every 10 seconds automatically`
- `Detection: Infrared ball sensor`

Report which ones are present and which are missing.

If any are MISSING, stop and tell the user. It most likely means the draft theme
is out of date and needs to be re-synced from the live theme before this work
proceeds. Do not improvise a replacement edit for a string you cannot find.

If all are present, continue to Task 1.

---

# TASK 1 - Features accordion

Block: `sections.main.blocks.collapsible_tab_UDXTX9`, setting `content`.

DELETE this list item entirely:
`<li><strong>Smart Auto-Launch</strong> — Infrared sensor fires the ball every 10 seconds automatically</li>`

INSERT in its place these three items:
`<li><strong>Fires on every ball drop</strong> - no timer and no remote. Drop a ball in and it launches, so a dog that learns to load it can run the game alone.</li><li><strong>Random distance mode (Upgraded)</strong> - hold the Distance Setting button for 3 seconds and the throw varies across all three distances</li><li><strong>Auto standby</strong> - powers down after about 30 minutes unused. Hold Distance Setting for 3 seconds to wake it.</li>`

ALSO in the same `content` string:
- Change `Lasts 3-4 hours on 2800mAh` to `Upgraded lasts about 5 to 6 hours per charge`
- Change `Upgraded: 6m, 10m, or 14m (20, 33, 46 ft)` to `Upgraded: 6m, 10m or 14m (19, 32, 45 ft)`

---

# TASK 2 - Specifications accordion

Block: `sections.main.blocks.collapsible_tab_GreT7C`, setting `content`.

DELETE these two lines from BOTH the Classic list and the Upgraded list
(four deletions in total):
`<li>Auto-Launch Interval: Every 10 seconds</li>`
`<li>Detection: Infrared ball sensor</li>`

DELETE from both lists:
`<li>Battery: 2800mAh rechargeable battery</li>`

CLASSIC list, additional changes:
- `<li><strong>Ball Size:</strong> 48mm/2inch soft tennis balls</li>`
  becomes `<li><strong>Ball Size:</strong> 48 to 50mm soft balls</li>`
- Add `<li>Launch Trigger: fires about 5 seconds after a ball is dropped in</li>`
- Add `<li>Indicator Light: flashing red when a ball is inside or launching, green when empty</li>`

UPGRADED list, additional changes:
- `<li>Ball Size: 58mm/2.28inch ETPU balls</li>`
  becomes `<li>Ball Size: 54 to 58mm (2.13 to 2.28 in) ETPU balls</li>`
- `<li>Launch Distances: 6, 10, 14m (20, 33, 46 ft)</li>`
  becomes `<li>Launch Distances: 6, 10, 14m (19, 32, 45 ft)</li>`
- Add `<li>Battery: USB-C rechargeable, about 5 to 6 hours play, about 6 hours charge</li>`
- Add `<li>Random Distance Mode: yes, hold Distance Setting for 3 seconds</li>`
- Add `<li>Launch Trigger: fires with no delay when a ball is dropped in</li>`

BOTH lists, add these two items:
`<li>Safety Sensor: none. Keep the launch path clear.</li>`
`<li>Auto Standby: after about 30 minutes unused</li>`

---

# TASK 3 - Hero text under the product

Section: `sections.rich_text_6mpUN9`, block `text_HeCUiU`, setting `text`.

REPLACE the entire value with:
`<p>The <strong>FetchMate</strong>&trade; does the throwing so your arm does not have to.</p><p>Drop a ball in and it fires straight away. Once your dog learns to drop the ball in themselves, they can <strong>run the whole game</strong> without you.</p>`

ALSO in section `rich_text_6mpUN9`, block `heading_4qbVbb`:
change `"heading_size": "h1"` to `"heading_size": "h2"`.

---

# TASK 4 - Four-column feature strip

Section `sections.multicolumn_nLHK4B`, block `column_EpmRyw`.

- `title` becomes `🎲 Random distance mode (Upgraded)`
- `text` becomes `<p>Hold the distance button for 3 seconds and the launcher mixes up the throw across all three distances, so your dog never knows what is coming.</p>`

Same section, block `column_9t9eXe`, setting `text`:
change `3-4 hours life` to `up to 5 to 6 hours of play`.

Same section, block `column_CC4qyF`, setting `text`:
change `48mm (2\")` to `48 to 50mm` and `58mm (2.28\")` to `54 to 58mm`.

Same section settings: change `"heading_size": "h1"` to `"heading_size": "h2"`.

---

# TASK 5 - Two large text/image sections

Section `sections.lumin_mega_LjFxmR`, block `text_hBdbkb`, setting `text`:
find the phrase `smart infrared detection` and replace it with `three launch distances`.
Also block `heading_RTfQGY`: `"heading_size": "h1"` becomes `"h2"`.

Section `sections.lumin_mega_qNV8xq`, block `heading_Rqt7Bc`:
`"heading_size": "h1"` becomes `"h2"`.

---

# TASK 6 - FetchMate Insights columns

Section `sections.custom_columns_wj766j`, block `icon_with_text_naBAkH`, setting `text`.

REPLACE the entire value with:
`<p>Drop a ball in and it launches immediately, one ball at a time. There is no timer and no remote, so your dog quickly learns the loop and runs the whole game themselves. The light flashes red when a ball is on its way.</p>`

Same section, block `heading_myc8Lz`: `"heading_size": "h1"` becomes `"h2"`.

---

# TASK 7 - Why Choose Us table

Section `sections.comparison_table_pFrHmC`, block `row_P7CGYM`:
setting `benefit` changes from `Infrared auto-detection` to `Random distance mode`.

Same section settings: `"heading_size": "h1"` becomes `"h2"`.

---

# TASK 8 - Comparison table custom liquid

Section `sections.custom_liquid_q73bfX`, setting `custom_liquid`.
This is a long escaped HTML string. Make these four replacements inside it:

- `48mm / 2&Prime; soft tennis balls` becomes `48-50mm soft balls`
- `58mm / 2.25&Prime; ETPU balls` becomes `54-58mm / 2.13-2.28&Prime; ETPU balls`
- In the UPGRADED distance bars only, `10m / 33ft` becomes `10m / 32ft`
  and `14m / 46ft` becomes `14m / 45ft` and the first Upgraded bar
  `6m / 20ft` becomes `6m / 19ft`.
- Leave the three CLASSIC bars (3m / 10ft, 6m / 20ft, 9m / 30ft) unchanged.

Note the Upgraded and Classic both contain a `6m / 20ft` bar. Only change the one
inside the `frm-cell-upgraded` cell.

---

# TASK 9 - What's Included and Care + Safety

Block `sections.main.blocks.collapsible_tab_UNKeUR`, setting `content`:
change `(48mm tennis balls for Classic / 58mm ETPU balls for Upgraded)` to
`(48 to 50mm balls for Classic / 54 to 58mm ETPU balls for Upgraded)`.

Block `sections.main.blocks.collapsible_tab_qMAYG7`, setting `content`:
- Change `Both the 48mm (2\") and 58mm (2.28\") balls` to
  `Both the 48 to 50mm and 54 to 58mm balls`
- Add these two list items as the FIRST two items of the first `<ul>`:
  `<li><strong>No safety sensor</strong> - this launcher cannot detect what is in front of it. Always set it up firing away from where your dog and other people stand.</li>`
  `<li><strong>Never put your hand into the launch pocket.</strong> If a ball jams, switch the unit off before removing it.</li>`
- Add to the second `<ul>` (Caring for Your Launcher):
  `<li>Do not use in rain or snow, do not pour water onto it, and do not leave it outdoors</li>`
  `<li>The launcher cannot be used while it is charging. Charge fully, then unplug.</li>`

---

# TASK 10 - Replace the FAQ section

Section `sections.faq_6HVkFq`.

DELETE all five existing blocks and their `block_order` entries. They are generic
store FAQs, they duplicate the Shipping and Returns accordion higher on the page,
and `collapsible_row_3nw4Nm` wrongly says warehouses are in China while the About
section lower on the same page says Australia.

REPLACE the section's `blocks` and `block_order` with exactly this. Do not change
the section's `settings` object.

```json
"blocks": {
    "faq_balls": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Can I use regular tennis balls with the FetchMate?",
        "icon": "check_mark",
        "row_content": "<p>No. Each version takes one specific ball size and standard tennis balls are too large for the launch chute. The Classic takes balls 48 to 50mm in diameter and the Upgraded takes ETPU balls 54 to 58mm (2.13 to 2.28 inches). Six balls are supplied with each version. Using the wrong size will jam the launch pocket.</p>",
        "page": ""
      }
    },
    "faq_version": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Should I get the Classic or the Upgraded FetchMate?",
        "icon": "check_mark",
        "row_content": "<p>Pick the Classic for small to medium dogs and indoor or compact spaces: it takes 48 to 50mm balls and launches 10, 20 or 30 feet. Pick the Upgraded for medium to large dogs and open outdoor space: it takes 54 to 58mm ETPU balls and launches 19, 32 or 45 feet. The Upgraded also has a random distance mode that varies the throw between all three settings.</p>",
        "page": ""
      }
    },
    "faq_largedogs": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Is the FetchMate suitable for large dogs like Labradors and German Shepherds?",
        "icon": "check_mark",
        "row_content": "<p>Choose the Upgraded FetchMate for large breeds. Its 54 to 58mm ETPU balls suit larger mouths and its 45 foot maximum throw gives a big dog a real run. The Classic's 48 to 50mm balls are sized for small to medium dogs. As with any ball toy, never use a ball small enough to fit fully behind your dog's back teeth, and supervise play.</p>",
        "page": ""
      }
    },
    "faq_sensor": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Does the FetchMate have a safety sensor that stops it firing at my dog?",
        "icon": "check_mark",
        "row_content": "<p>No. Neither version has a motion or obstacle sensor. The light on the front is a status indicator, not a safety sensor: it flashes red when a ball is inside or being launched and shows green when the launcher is empty. Because the machine cannot detect what is in front of it, always position it so it fires away from where your dog and other people stand.</p>",
        "page": ""
      }
    },
    "faq_hit": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Will my dog get hit by the ball?",
        "icon": "check_mark",
        "row_content": "<p>It can happen, because the FetchMate has no sensor to stop it firing when something is in front. Dogs often stand right at the chute while they are learning. Aim the launcher away from where your dog waits, start on the lowest distance setting, and if your dog crowds the front, raise the unit onto a low table or step so the ball launches over their head. Watch the indicator light, which flashes red when a ball is about to launch.</p>",
        "page": ""
      }
    },
    "faq_autolaunch": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Does the FetchMate launch balls automatically on a timer?",
        "icon": "check_mark",
        "row_content": "<p>No. It fires each time a ball is dropped into the hole on top, one ball at a time, so there is no timer to set. On the Classic the ball launches about 5 seconds after it goes in, and you wait for the internal roller to stop before dropping the next one. On the Upgraded the ball launches with no delay and the next ball can go in after about 4 seconds.</p>",
        "page": ""
      }
    },
    "faq_training": {
      "type": "collapsible_row",
      "settings": {
        "heading": "How do I teach my dog to load the ball themselves?",
        "icon": "check_mark",
        "row_content": "<p>Both versions fire whenever a ball is dropped in, so a dog that learns to drop the ball can run the game alone. Start by dropping the ball in yourself while your dog watches, so they connect the drop with the launch. Next, hold a ball over the opening and reward your dog for touching or mouthing it. Then reward them for releasing the ball into the hole from your hand, and finally from the ground beside the machine. Most dogs pick it up in a few short sessions.</p>",
        "page": ""
      }
    },
    "faq_safety": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Are automatic ball launchers bad for dogs?",
        "icon": "check_mark",
        "row_content": "<p>Used sensibly they are fine, but unlimited high-speed fetch can strain joints and encourage obsessive behaviour. Vets and canine physiotherapists advise short sessions, a warm up first, soft surfaces such as grass where possible, and ending the game before your dog is exhausted. With the FetchMate, start on the shortest distance setting, keep sessions to roughly 10 to 15 minutes, and stop the game yourself rather than letting your dog decide.</p>",
        "page": ""
      }
    },
    "faq_jam": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Why is the ball not launching, or getting stuck?",
        "icon": "check_mark",
        "row_content": "<p>The usual cause is a wet, slobbery, dirty or damaged ball, since moisture and grit reduce grip on the drive rollers. Wipe balls dry between throws, rotate through the six supplied balls so each has time to dry, and retire any ball that is split or badly chewed. If a ball jams in the launch pocket, switch the unit off before removing it, and never put your hand into the pocket while it is powered on.</p>",
        "page": ""
      }
    },
    "faq_stopped": {
      "type": "collapsible_row",
      "settings": {
        "heading": "My FetchMate stopped working by itself. What happened?",
        "icon": "check_mark",
        "row_content": "<p>It has most likely gone into standby. Both versions power down automatically after about 30 minutes without use, even with the bottom switch still on, which saves battery. Hold the Distance Setting button for 3 seconds to wake it up. If the indicator is solid red the battery is below 25 percent and the unit will shut down on its own, so recharge it and restart with the ON/OFF button.</p>",
        "page": ""
      }
    },
    "faq_charging": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Can the FetchMate be used while it is charging?",
        "icon": "check_mark",
        "row_content": "<p>No. Neither version will operate while plugged in. Charge it fully, unplug the cable, then start your session. Use a 5V 2A to 3A adapter with the supplied USB-A to USB-C cable.</p>",
        "page": ""
      }
    },
    "faq_battery": {
      "type": "collapsible_row",
      "settings": {
        "heading": "How long does the FetchMate battery last?",
        "icon": "check_mark",
        "row_content": "<p>The Upgraded gives about 5 to 6 hours of play from a full charge, which takes about 6 hours with a 5V 2A adapter. Both versions charge over USB-C and show battery level through the indicator light: red is below 25 percent, yellow is 25 to 90 percent, and green is above 90 percent. A blinking light means it is charging.</p>",
        "page": ""
      }
    },
    "faq_indoors": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Can the FetchMate be used indoors?",
        "icon": "check_mark",
        "row_content": "<p>The Classic suits indoor play well on its 10 foot setting. The Upgraded is designed for outdoor use because it throws much further, so indoors you should keep it on Distance 1, which is 19 feet, and only in a long clear space such as a hallway. Clear fragile items from the launch path either way.</p>",
        "page": ""
      }
    },
    "faq_puppies": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Is the FetchMate safe for puppies and senior dogs?",
        "icon": "check_mark",
        "row_content": "<p>The supplied balls are softer than a regulation tennis ball, which is gentler on developing and ageing teeth. Keep sessions short and stay on the lowest distance setting for both puppies and seniors, since repeated sprinting and sudden turns are hard on growing joints and arthritic ones. Supervise play and remove any ball that starts to break apart. If your dog has a joint, heart or breathing condition, check with your vet first.</p>",
        "page": ""
      }
    },
    "faq_waterproof": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Is the FetchMate waterproof?",
        "icon": "check_mark",
        "row_content": "<p>No. Do not use it in rain or snow, do not pour water onto it, and do not leave it outdoors. Wipe it with a dry or slightly damp cloth and never submerge it. Wet or dirty balls should not be fed into the machine either, because moisture affects the drive rollers and shortens the throw.</p>",
        "page": ""
      }
    },
    "faq_spares": {
      "type": "collapsible_row",
      "settings": {
        "heading": "Can I buy replacement balls for the FetchMate?",
        "icon": "check_mark",
        "row_content": "<p>Yes. Replacement balls are sold in packs of six for both versions: 48mm for the Classic and 58mm for the Upgraded. Keeping spares means you can rotate balls so each has time to dry between throws, which is the simplest way to avoid jams and short launches.</p>",
        "page": ""
      }
    }
  },
  "block_order": [
    "faq_balls",
    "faq_version",
    "faq_largedogs",
    "faq_sensor",
    "faq_hit",
    "faq_autolaunch",
    "faq_training",
    "faq_safety",
    "faq_jam",
    "faq_stopped",
    "faq_charging",
    "faq_battery",
    "faq_indoors",
    "faq_puppies",
    "faq_waterproof",
    "faq_spares"
  ]
```

Also in that section's settings: `"heading_size": "h1"` becomes `"h2"`.

---

# TASK 11 - Create the FAQ schema snippet

Create a new file `snippets/faq-fetchmate.liquid` containing exactly:

```liquid
{%- comment -%} FAQPage schema for the FetchMate PDP {%- endcomment -%}
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "@id": "{{ shop.url }}{{ product.url }}#faq",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Can I use regular tennis balls with the FetchMate?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. Each version takes one specific ball size and standard tennis balls are too large for the launch chute. The Classic takes balls 48 to 50mm in diameter and the Upgraded takes ETPU balls 54 to 58mm (2.13 to 2.28 inches). Six balls are supplied with each version. Using the wrong size will jam the launch pocket."
      }
    },
    {
      "@type": "Question",
      "name": "Should I get the Classic or the Upgraded FetchMate?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Pick the Classic for small to medium dogs and indoor or compact spaces: it takes 48 to 50mm balls and launches 10, 20 or 30 feet. Pick the Upgraded for medium to large dogs and open outdoor space: it takes 54 to 58mm ETPU balls and launches 19, 32 or 45 feet. The Upgraded also has a random distance mode that varies the throw between all three settings."
      }
    },
    {
      "@type": "Question",
      "name": "Is the FetchMate suitable for large dogs like Labradors and German Shepherds?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Choose the Upgraded FetchMate for large breeds. Its 54 to 58mm ETPU balls suit larger mouths and its 45 foot maximum throw gives a big dog a real run. The Classic's 48 to 50mm balls are sized for small to medium dogs. As with any ball toy, never use a ball small enough to fit fully behind your dog's back teeth, and supervise play."
      }
    },
    {
      "@type": "Question",
      "name": "Does the FetchMate have a safety sensor that stops it firing at my dog?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. Neither version has a motion or obstacle sensor. The light on the front is a status indicator, not a safety sensor: it flashes red when a ball is inside or being launched and shows green when the launcher is empty. Because the machine cannot detect what is in front of it, always position it so it fires away from where your dog and other people stand."
      }
    },
    {
      "@type": "Question",
      "name": "Will my dog get hit by the ball?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "It can happen, because the FetchMate has no sensor to stop it firing when something is in front. Dogs often stand right at the chute while they are learning. Aim the launcher away from where your dog waits, start on the lowest distance setting, and if your dog crowds the front, raise the unit onto a low table or step so the ball launches over their head. Watch the indicator light, which flashes red when a ball is about to launch."
      }
    },
    {
      "@type": "Question",
      "name": "Does the FetchMate launch balls automatically on a timer?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. It fires each time a ball is dropped into the hole on top, one ball at a time, so there is no timer to set. On the Classic the ball launches about 5 seconds after it goes in, and you wait for the internal roller to stop before dropping the next one. On the Upgraded the ball launches with no delay and the next ball can go in after about 4 seconds."
      }
    },
    {
      "@type": "Question",
      "name": "How do I teach my dog to load the ball themselves?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Both versions fire whenever a ball is dropped in, so a dog that learns to drop the ball can run the game alone. Start by dropping the ball in yourself while your dog watches, so they connect the drop with the launch. Next, hold a ball over the opening and reward your dog for touching or mouthing it. Then reward them for releasing the ball into the hole from your hand, and finally from the ground beside the machine. Most dogs pick it up in a few short sessions."
      }
    },
    {
      "@type": "Question",
      "name": "Are automatic ball launchers bad for dogs?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Used sensibly they are fine, but unlimited high-speed fetch can strain joints and encourage obsessive behaviour. Vets and canine physiotherapists advise short sessions, a warm up first, soft surfaces such as grass where possible, and ending the game before your dog is exhausted. With the FetchMate, start on the shortest distance setting, keep sessions to roughly 10 to 15 minutes, and stop the game yourself rather than letting your dog decide."
      }
    },
    {
      "@type": "Question",
      "name": "Why is the ball not launching, or getting stuck?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The usual cause is a wet, slobbery, dirty or damaged ball, since moisture and grit reduce grip on the drive rollers. Wipe balls dry between throws, rotate through the six supplied balls so each has time to dry, and retire any ball that is split or badly chewed. If a ball jams in the launch pocket, switch the unit off before removing it, and never put your hand into the pocket while it is powered on."
      }
    },
    {
      "@type": "Question",
      "name": "My FetchMate stopped working by itself. What happened?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "It has most likely gone into standby. Both versions power down automatically after about 30 minutes without use, even with the bottom switch still on, which saves battery. Hold the Distance Setting button for 3 seconds to wake it up. If the indicator is solid red the battery is below 25 percent and the unit will shut down on its own, so recharge it and restart with the ON/OFF button."
      }
    },
    {
      "@type": "Question",
      "name": "Can the FetchMate be used while it is charging?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. Neither version will operate while plugged in. Charge it fully, unplug the cable, then start your session. Use a 5V 2A to 3A adapter with the supplied USB-A to USB-C cable."
      }
    },
    {
      "@type": "Question",
      "name": "How long does the FetchMate battery last?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The Upgraded gives about 5 to 6 hours of play from a full charge, which takes about 6 hours with a 5V 2A adapter. Both versions charge over USB-C and show battery level through the indicator light: red is below 25 percent, yellow is 25 to 90 percent, and green is above 90 percent. A blinking light means it is charging."
      }
    },
    {
      "@type": "Question",
      "name": "Can the FetchMate be used indoors?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The Classic suits indoor play well on its 10 foot setting. The Upgraded is designed for outdoor use because it throws much further, so indoors you should keep it on Distance 1, which is 19 feet, and only in a long clear space such as a hallway. Clear fragile items from the launch path either way."
      }
    },
    {
      "@type": "Question",
      "name": "Is the FetchMate safe for puppies and senior dogs?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The supplied balls are softer than a regulation tennis ball, which is gentler on developing and ageing teeth. Keep sessions short and stay on the lowest distance setting for both puppies and seniors, since repeated sprinting and sudden turns are hard on growing joints and arthritic ones. Supervise play and remove any ball that starts to break apart. If your dog has a joint, heart or breathing condition, check with your vet first."
      }
    },
    {
      "@type": "Question",
      "name": "Is the FetchMate waterproof?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. Do not use it in rain or snow, do not pour water onto it, and do not leave it outdoors. Wipe it with a dry or slightly damp cloth and never submerge it. Wet or dirty balls should not be fed into the machine either, because moisture affects the drive rollers and shortens the throw."
      }
    },
    {
      "@type": "Question",
      "name": "Can I buy replacement balls for the FetchMate?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes. Replacement balls are sold in packs of six for both versions: 48mm for the Classic and 58mm for the Upgraded. Keeping spares means you can rotate balls so each has time to dry between throws, which is the simplest way to avoid jams and short launches."
      }
    }
  ]
}
</script>
```

Then render it. Open `sections/faq.liquid` and add this immediately before the
closing `{% schema %}` tag, or if that is awkward, add it at the very end of
`sections/main-product.liquid` before its `{% schema %}` tag:

```liquid
{%- if product.template_suffix == 'fetchmate-2' -%}
  {% render 'faq-fetchmate' %}
{%- endif -%}
```

If neither file exists or the structure differs, tell the user rather than
guessing, and suggest the closest safe location.

---

# TASK 12 - Star ratings in search results (optional but high value)

The store has Loox review data available on the product as metafields
`loox.avg_rating` (currently 4.8) and `loox.num_reviews` (currently 18), but no
aggregateRating is being output in schema.

Before adding anything, check whether the Smart SEO app or Loox already outputs
an `aggregateRating` on this page. If it does, STOP and tell the user, because
two aggregateRating blocks will cause a Google error.

If nothing outputs it, create `snippets/rating-fetchmate.liquid`:

```liquid
{%- assign r = product.metafields.loox.avg_rating.value -%}
{%- assign n = product.metafields.loox.num_reviews.value -%}
{%- if r and n and n > 0 -%}
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Product",
  "@id": "{{ shop.url }}{{ product.url }}#product",
  "name": {{ product.title | json }},
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "{{ r }}",
    "reviewCount": "{{ n }}"
  }
}
</script>
{%- endif -%}
```

and render it the same way as Task 11.

---

# FINAL VERIFICATION

Run these and report the results to the user:

1. `python3 -c "import json,re; s=open('templates/product.fetchmate-2.json').read(); s=re.sub(r'^/\*.*?\*/','',s,flags=re.S); json.loads(s); print('valid JSON')"`
2. `grep -ci "infrared" templates/product.fetchmate-2.json` - must be 0
3. `grep -ci "10 seconds" templates/product.fetchmate-2.json` - must be 0
4. `grep -ci "2800mAh" templates/product.fetchmate-2.json` - must be 0
5. `grep -ci "China" templates/product.fetchmate-2.json` - must be 0
6. `grep -c '"heading_size": "h1"' templates/product.fetchmate-2.json` - must be 0
7. Confirm `snippets/faq-fetchmate.liquid` exists and contains 16 Question objects.

Then commit to `main` with a clear message so the changes sync to the draft theme,
and STOP.

Tell the user:
- which files changed, with a one line summary of each
- the results of all 7 checks above
- that the changes will appear on the DRAFT theme `RoverRituals-theme/main` in a
  minute or two, and they should use Preview on that theme to review the product
  page before publishing
- that publishing is their call, not yours

Then add this reminder in your own words: publishing the draft theme replaces the
live theme entirely. If anything was changed on the live theme through the Shopify
theme editor after this draft was created, those changes are not in this repo and
will be lost on publish. Advise the user to compare the two themes before
publishing, or to re-sync if they are unsure.

Do NOT publish the theme.
