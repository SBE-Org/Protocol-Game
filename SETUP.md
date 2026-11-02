# Shaggar Diplomat Challenge: setup (about 10 minutes)

You get two files:

- `index.html`: the game, the big-screen mode and the admin dashboard, in one page.
- `Code.gs`: a small script that saves every score into a Google Sheet you own.

Without step 1, the game still works, but each device keeps its own scores ("preview mode").
Step 1 is what makes phones and the big screen share one scoreboard.

## 1. Create the results sheet (once)

1. Go to sheets.google.com and create a blank sheet. Name it **Diplomat Challenge Results**.
2. In the sheet, open **Extensions → Apps Script**.
3. Delete what is in the editor, paste the whole of `Code.gs`, and change the password on the first line:
   `const ADMIN_PASSWORD = 'your-own-password';`
4. Click **Save**, choose `setup` in the function menu at the top, and click **Run**. Allow the permissions Google asks for.
   This creates three tabs: **Results**, **Answers** and **Events**.
5. Click **Deploy → New deployment**, choose type **Web app**, and set:
   - Execute as: **Me**
   - Who has access: **Anyone**
6. Click **Deploy** and copy the **Web app URL** (it ends in `/exec`).

## 2. Connect the game

Open `index.html` in a text editor, find this line near the top of the script, and paste your URL between the quotes:

```js
const API_URL = "";
```

## 3. Put it online

Upload `index.html` to your GitHub Pages repository, the same way as the spinner game.

## 4. On the day

| Who | Open this address |
| --- | --- |
| Guests on their phones | `https://your-site/` (share as a QR code) |
| Big screen | `https://your-site/#screen` |
| Admin (you) | `https://your-site/#admin` and enter your password |

- On the admin page, choose **Round 1**, **Round 2** or **Round 3** to open it for everyone, or **Closed** between rounds. Phones and the screen pick up the change within about 12 seconds.
- Round 1 is Lucky Bowl, Round 2 is Stamp It (21 seconds per question), Round 3 is Road to COP32.
- Each person plays each round once, whether on a phone or on the big screen. Their score follows their name across devices.
- Phones remember who is playing. On the big screen, each player picks their name and taps **Next player** when done.
- People not on the list can type their name and play as a guest.

## Changing things later

- **Password:** edit `ADMIN_PASSWORD` in Apps Script, then **Deploy → Manage deployments → Edit → New version**.
- **Guest list:** the names are in `index.html` in the `GUESTS` list.
- **All raw data** (every score, answer and tap count, with times) is in the Google Sheet, ready to filter or export.
- If you edit `Code.gs`, always publish a **new version** of the deployment, or the old code keeps running.
