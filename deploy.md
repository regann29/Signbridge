# Putting SignBridge online

SignBridge is a static website. Nothing needs to run on a server, so you only need a place to host files. The build step creates the finished site in a folder called `dist`.

**Before you start:** the build downloads a small hand model file from Google's public MediaPipe storage the first time. All the hosts below can do this. If you ever need to host the file yourself, set `MODEL_URL` to your own copy.

**One thing to know about the camera:** browsers only allow camera and microphone access on secure pages (https), which every host below provides.

## 1. Put the code on GitHub

Create an empty repository on github.com (for example `signbridge`, with no README), then run this in the project folder:

```
git init
git add .
git commit -m "First version of SignBridge"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/signbridge.git
git push -u origin main
```

The `.gitignore` file keeps `node_modules`, `dist` and downloaded files out of the repository on purpose.

## 2. Choose a host

### GitHub Pages (free, easiest if you already use GitHub)

1. In your repository open **Settings, then Pages**.
2. Under **Source**, choose **GitHub Actions**.
3. Push to `main`. The workflow in `.github/workflows/pages.yml` builds the site and publishes it.
4. Your address will look like `https://YOUR-USERNAME.github.io/signbridge/`.

GitHub Pages cannot send custom security headers. SignBridge still ships its main protection, the Content Security Policy, inside the page itself, so the page can only load its own files. The extra headers (blocking framing, limiting camera access to the site, and so on) are not applied there. If you want the full set, use Netlify, Vercel or Cloudflare Pages.

### Netlify

1. On netlify.com choose **Add new site, then Import an existing project**, and pick your GitHub repository.
2. The settings are read from `netlify.toml`. You don't need to change anything.
3. Click **Deploy**.

### Vercel

1. On vercel.com choose **Add New, then Project**, and import your repository.
2. The settings are read from `vercel.json`. Leave the framework as **Other**.
3. Click **Deploy**.

### Cloudflare Pages

1. In the Cloudflare dashboard open **Workers & Pages, then Create, then Pages, then Connect to Git**.
2. Build command: `npm ci && npm run build`. Output folder: `dist`.
3. Click **Save and Deploy**. Security headers are read from the generated `_headers` file.

## 3. Check your live site

Open the address in Chrome or Edge, then:

1. Go to **Sign to speech** and press **Start camera**. Allow the camera when asked. Hand tracking should say "ready".
2. Teach two signs and press **Start recognition**.
3. Open the browser's developer tools (F12), look at the **Console** tab, and make sure there are no red messages about "Content Security Policy". If there are, please open an issue with the message.

Only after this check can you say the site works for real. Hand tracking runs inside the browser, and the automated tests cannot cover it.

## Using your own domain

Every host above has a **Domains** section where you can add your own address. They set up https for you.

## If hand tracking says files are missing

The model download failed during the build. Check the build log, then redeploy. You can also set `MODEL_URL` as a build environment variable.
