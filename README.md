<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Minimal Gallery</title>
    <style>
      :root {
        --bg: #f5f5f5;
        --bg-alt: #ffffff;
        --accent: #111827;
        --accent-soft: #e5e7eb;
        --text-main: #111827;
        --text-muted: #6b7280;
        --danger: #ef4444;
        --radius-lg: 18px;
        --radius-md: 12px;
        --shadow-soft: 0 18px 45px rgba(15, 23, 42, 0.12);
        --shadow-subtle: 0 8px 24px rgba(15, 23, 42, 0.06);
        --transition-fast: 0.18s ease-out;
      }

      *,
      *::before,
      *::after {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        min-height: 100vh;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, "SF Pro Text",
          "Segoe UI", sans-serif;
        background: radial-gradient(circle at top left, #e5e7eb, #f9fafb 45%)
            no-repeat,
          var(--bg);
        color: var(--text-main);
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 24px;
      }

      .app-shell {
        width: 100%;
        max-width: 1080px;
        background: rgba(255, 255, 255, 0.9);
        backdrop-filter: blur(18px);
        border-radius: 28px;
        box-shadow: var(--shadow-soft);
        padding: 24px;
        display: grid;
        grid-template-columns: minmax(0, 1.15fr) minmax(0, 1.5fr);
        gap: 24px;
      }

      @media (max-width: 900px) {
        .app-shell {
          grid-template-columns: 1fr;
          padding: 20px;
        }
      }

      .brand {
        display: flex;
        align-items: center;
        gap: 10px;
        margin-bottom: 32px;
      }

      .brand-mark {
        width: 32px;
        height: 32px;
        border-radius: 999px;
        background: linear-gradient(135deg, #0f172a, #4b5563);
        display: flex;
        align-items: center;
        justify-content: center;
        color: #f9fafb;
        font-size: 18px;
        font-weight: 600;
      }

      .brand-text {
        display: flex;
        flex-direction: column;
        gap: 2px;
      }

      .brand-name {
        font-size: 15px;
        letter-spacing: 0.12em;
        text-transform: uppercase;
      }

      .brand-tagline {
        font-size: 12px;
        color: var(--text-muted);
      }

      .auth-card {
        background: var(--bg-alt);
        border-radius: var(--radius-lg);
        padding: 24px 24px 22px;
        box-shadow: var(--shadow-subtle);
        display: flex;
        flex-direction: column;
        gap: 18px;
        align-self: center;
      }

      .auth-toggle {
        display: inline-flex;
        align-self: flex-start;
        background: #f3f4f6;
        border-radius: 999px;
        padding: 4px;
        gap: 4px;
      }

      .auth-tab {
        border: none;
        padding: 8px 18px;
        font-size: 13px;
        border-radius: 999px;
        background: transparent;
        color: var(--text-muted);
        cursor: pointer;
        transition: background var(--transition-fast),
          color var(--transition-fast), transform var(--transition-fast);
      }

      .auth-tab.active {
        background: #ffffff;
        color: var(--text-main);
        transform: translateY(-1px);
        box-shadow: 0 8px 24px rgba(15, 23, 42, 0.18);
      }

      .auth-heading {
        display: flex;
        flex-direction: column;
        gap: 6px;
      }

      .auth-heading h1 {
        margin: 0;
        font-size: 24px;
        letter-spacing: -0.03em;
      }

      .auth-heading p {
        margin: 0;
        font-size: 13px;
        color: var(--text-muted);
      }

      .auth-form {
        display: flex;
        flex-direction: column;
        gap: 12px;
      }

      .field {
        display: flex;
        flex-direction: column;
        gap: 6px;
      }

      .field-label {
        font-size: 12px;
        color: var(--text-muted);
      }

      .field-input {
        position: relative;
      }

      .field-input input {
        width: 100%;
        border-radius: 999px;
        border: 1px solid #e5e7eb;
        padding: 9px 14px;
        font-size: 13px;
        outline: none;
        background: #f9fafb;
        transition: border-color var(--transition-fast),
          box-shadow var(--transition-fast), background var(--transition-fast);
      }

      .field-input input:focus {
        border-color: #111827;
        background: #ffffff;
        box-shadow: 0 0 0 1px #11182718;
      }

      .field-input input::placeholder {
        color: #9ca3af;
      }

      .auth-footer {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 10px;
        margin-top: 6px;
      }

      .remember {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        font-size: 12px;
        color: var(--text-muted);
      }

      .remember input {
        width: 14px;
        height: 14px;
        border-radius: 4px;
        border: 1px solid #d1d5db;
      }

      .link-muted {
        font-size: 12px;
        color: var(--text-muted);
        text-decoration: underline;
        text-decoration-thickness: 1px;
        text-underline-offset: 3px;
        cursor: pointer;
      }

      .primary-button {
        width: 100%;
        border-radius: 999px;
        border: none;
        padding: 9px 14px;
        font-size: 13px;
        font-weight: 500;
        letter-spacing: 0.06em;
        text-transform: uppercase;
        background: #111827;
        color: #f9fafb;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 6px;
        box-shadow: 0 12px 30px rgba(15, 23, 42, 0.55);
        transition: transform 0.14s ease-out, box-shadow 0.14s ease-out,
          background var(--transition-fast);
      }

      .primary-button:hover {
        transform: translateY(-1px);
        box-shadow: 0 18px 40px rgba(15, 23, 42, 0.6);
      }

      .primary-button:active {
        transform: translateY(0);
        box-shadow: 0 8px 24px rgba(15, 23, 42, 0.35);
      }

      .pill-text {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        padding: 6px 12px;
        border-radius: 999px;
        background: #f3f4f6;
        color: var(--text-muted);
        font-size: 11px;
      }

      .pill-dot {
        width: 6px;
        height: 6px;
        border-radius: 999px;
        background: #10b981;
      }

      .auth-meta {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 10px;
        margin-top: 10px;
      }

      .auth-meta span {
        font-size: 11px;
        color: var(--text-muted);
      }

      .auth-error {
        font-size: 12px;
        color: var(--danger);
        background: rgba(239, 68, 68, 0.06);
        border-radius: 999px;
        padding: 6px 10px;
        display: none;
      }

      .auth-error.visible {
        display: inline-flex;
        align-items: center;
        gap: 6px;
      }

      .auth-error-dot {
        width: 7px;
        height: 7px;
        border-radius: 999px;
        background: var(--danger);
      }

      .gallery-panel {
        border-radius: var(--radius-lg);
        padding: 18px 18px 18px 20px;
        background: radial-gradient(circle at 0% 0%, #111827, #020617 60%);
        color: #e5e7eb;
        position: relative;
        overflow: hidden;
        display: flex;
        flex-direction: column;
        gap: 16px;
      }

      .gallery-panel::before {
        content: "";
        position: absolute;
        inset: -30%;
        background:
          radial-gradient(circle at 0% 0%, rgba(248, 250, 252, 0.08) 0, transparent 50%),
          radial-gradient(circle at 100% 20%, rgba(56, 189, 248, 0.18) 0, transparent 52%),
          radial-gradient(circle at 40% 100%, rgba(248, 250, 252, 0.08) 0, transparent 48%);
        opacity: 0.75;
        pointer-events: none;
      }

      .gallery-header,
      .gallery-footer {
        position: relative;
        z-index: 1;
      }

      .gallery-header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 12px;
      }

      .gallery-title {
        display: flex;
        flex-direction: column;
        gap: 4px;
      }

      .gallery-title h2 {
        margin: 0;
        font-size: 17px;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .gallery-title span {
        font-size: 12px;
        color: #9ca3af;
      }

      .user-chip {
        display: flex;
        align-items: center;
        gap: 8px;
        background: rgba(15, 23, 42, 0.72);
        border-radius: 999px;
        padding: 6px 10px 6px 6px;
        border: 1px solid rgba(148, 163, 184, 0.5);
      }

      .user-avatar {
        width: 24px;
        height: 24px;
        border-radius: 999px;
        background: linear-gradient(135deg, #f97316, #facc15);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 13px;
        font-weight: 600;
        color: #111827;
      }

      .user-meta {
        display: flex;
        flex-direction: column;
        gap: 2px;
      }

      .user-meta strong {
        font-size: 12px;
      }

      .user-meta span {
        font-size: 11px;
        color: #9ca3af;
      }

      .user-logout {
        margin-left: 4px;
        font-size: 11px;
        color: #9ca3af;
        cursor: pointer;
        text-decoration: underline;
        text-decoration-thickness: 1px;
        text-underline-offset: 3px;
      }

      .gallery-grid-wrapper {
        position: relative;
        z-index: 1;
        flex: 1;
        min-height: 230px;
      }

      .gallery-grid {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 12px;
        height: 100%;
      }

      .photo-card {
        position: relative;
        border-radius: var(--radius-md);
        overflow: hidden;
        background: rgba(15, 23, 42, 0.9);
        cursor: pointer;
        transition: transform 0.18s ease-out, box-shadow 0.18s ease-out,
          border-color 0.18s ease-out;
        border: 1px solid transparent;
        display: flex;
        flex-direction: column;
      }

      .photo-card:hover {
        transform: translateY(-4px);
        box-shadow: 0 18px 45px rgba(15, 23, 42, 0.85);
        border-color: rgba(148, 163, 184, 0.8);
      }

      .photo-media {
        position: relative;
        padding-bottom: 130%;
        overflow: hidden;
      }

      .photo-media img {
        position: absolute;
        inset: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        filter: saturate(1.15);
        transform: scale(1.02);
        transition: transform 0.6s ease-out, filter 0.6s ease-out;
      }

      .photo-card:hover .photo-media img {
        transform: scale(1.08);
        filter: saturate(1.3);
      }

      .photo-overlay {
        position: absolute;
        inset: 0;
        background: radial-gradient(
          circle at 0% 0%,
          rgba(15, 23, 42, 0) 0,
          rgba(15, 23, 42, 0.3) 56%
        );
        opacity: 0;
        transition: opacity 0.2s ease-out;
      }

      .photo-card:hover .photo-overlay {
        opacity: 1;
      }

      .photo-footer {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 8px 9px 8px 9px;
        backdrop-filter: blur(14px);
        background: linear-gradient(
          to top,
          rgba(15, 23, 42, 0.95),
          rgba(15, 23, 42, 0.8)
        );
      }

      .photo-meta {
        display: flex;
        flex-direction: column;
        gap: 2px;
      }

      .photo-title {
        font-size: 12px;
      }

      .photo-subtitle {
        font-size: 11px;
        color: #9ca3af;
      }

      .photo-actions {
        display: inline-flex;
        align-items: center;
        gap: 6px;
      }

      .chip {
        border-radius: 999px;
        border: 1px solid rgba(148, 163, 184, 0.7);
        padding: 3px 7px 3px 5px;
        font-size: 10px;
        display: inline-flex;
        align-items: center;
        gap: 4px;
        color: #e5e7eb;
        background: rgba(15, 23, 42, 0.9);
      }

      .chip-dot {
        width: 6px;
        height: 6px;
        border-radius: 999px;
      }

      .chip-dot.green {
        background: #22c55e;
      }

      .chip-dot.blue {
        background: #38bdf8;
      }

      .like-button {
        border-radius: 999px;
        width: 26px;
        height: 26px;
        border: 1px solid rgba(148, 163, 184, 0.7);
        display: inline-flex;
        align-items: center;
        justify-content: center;
        font-size: 12px;
        background: rgba(15, 23, 42, 0.9);
        color: #f9fafb;
        cursor: pointer;
        transition: background 0.18s ease-out, transform 0.12s ease-out,
          border-color 0.18s ease-out;
      }

      .like-button.liked {
        background: #f97316;
        border-color: transparent;
        transform: translateY(-1px);
      }

      .gallery-footer {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 10px;
        font-size: 11px;
        color: #9ca3af;
      }

      .gallery-footer span {
        display: inline-flex;
        align-items: center;
        gap: 4px;
      }

      .dot-mini {
        width: 4px;
        height: 4px;
        border-radius: 999px;
        background: rgba(148, 163, 184, 0.9);
      }

      .gallery-hint {
        display: inline-flex;
        align-items: center;
        gap: 6px;
      }

      .hint-key {
        border-radius: 6px;
        border: 1px solid rgba(148, 163, 184, 0.7);
        padding: 2px 6px;
        font-size: 10px;
      }

      @media (max-width: 600px) {
        body {
          padding: 16px;
        }

        .app-shell {
          padding: 16px;
          border-radius: 22px;
        }

        .gallery-grid {
          grid-template-columns: repeat(2, minmax(0, 1fr));
        }

        .gallery-panel {
          padding: 16px;
        }

        .auth-card {
          padding: 18px 18px 16px;
        }
      }

      @media (max-width: 420px) {
        .gallery-grid {
          grid-template-columns: repeat(1, minmax(0, 1fr));
        }

        .gallery-header {
          flex-direction: column;
          align-items: flex-start;
        }

        .auth-footer {
          flex-direction: column;
          align-items: flex-start;
        }
      }
    </style>
  </head>
  <body>
    <main class="app-shell">
      <section>
        <header class="brand">
          <div class="brand-mark">M</div>
          <div class="brand-text">
            <span class="brand-name">Minimalist</span>
            <span class="brand-tagline">Quiet spaces for your photos</span>
          </div>
        </header>

        <div class="auth-card" id="authCard">
          <div class="auth-toggle">
            <button
              class="auth-tab active"
              id="tabLogin"
              type="button"
              aria-pressed="true"
            >
              Log in
            </button>
            <button
              class="auth-tab"
              id="tabSignup"
              type="button"
              aria-pressed="false"
            >
              Sign up
            </button>
          </div>

          <div class="auth-heading">
            <h1 id="authTitle">Welcome back</h1>
            <p id="authSubtitle">
              Enter your details to continue to the gallery.
            </p>
          </div>

          <form class="auth-form" id="authForm">
            <div class="field" id="nameField" style="display: none">
              <label class="field-label" for="nameInput">Name</label>
              <div class="field-input">
                <input
                  id="nameInput"
                  type="text"
                  placeholder="How should we call you?"
                  autocomplete="name"
                />
              </div>
            </div>

            <div class="field">
              <label class="field-label" for="emailInput">Email</label>
              <div class="field-input">
                <input
                  id="emailInput"
                  type="email"
                  placeholder="you@example.com"
                  autocomplete="email"
                  required
                />
              </div>
            </div>

            <div class="field">
              <label class="field-label" for="passwordInput">Password</label>
              <div class="field-input">
                <input
                  id="passwordInput"
                  type="password"
                  placeholder="At least 6 characters"
                  autocomplete="current-password"
                  required
                />
              </div>
            </div>

            <div class="auth-footer">
              <label class="remember">
                <input id="rememberInput" type="checkbox" />
                <span>Remember this device</span>
              </label>

              <span class="link-muted" id="switchLink">New here? Sign up</span>
            </div>

            <button class="primary-button" type="submit" id="authButton">
              <span id="authButtonText">Enter gallery</span>
              <span aria-hidden="true">→</span>
            </button>
          </form>

          <div class="auth-meta">
            <div class="pill-text">
              <span class="pill-dot"></span>
              Minimal UI — front‑end only demo
            </div>
            <span>We don't send or store real data.</span>
          </div>

          <div class="auth-error" id="authError">
            <span class="auth-error-dot"></span>
            <span id="authErrorText"></span>
          </div>
        </div>
      </section>

      <section class="gallery-panel" aria-live="polite">
        <div class="gallery-header">
          <div class="gallery-title">
            <h2>Calm gallery</h2>
            <span>Hover, tap, and favorite what you like.</span>
          </div>

          <div class="user-chip" id="userChip" style="display: none">
            <div class="user-avatar" id="userAvatar">M</div>
            <div class="user-meta">
              <strong id="userName">Guest</strong>
              <span>Signed in</span>
            </div>
            <button class="user-logout" type="button" id="logoutButton">
              log out
            </button>
          </div>
        </div>

        <div class="gallery-grid-wrapper">
          <div class="gallery-grid" id="galleryGrid" aria-label="Photo gallery">
            <!-- Cards will be injected via JavaScript -->
          </div>
        </div>

        <footer class="gallery-footer">
          <span>
            <span class="dot-mini"></span>
            Signed‑in state is stored only in this browser.
          </span>
          <span class="gallery-hint">
            <span class="hint-key">click</span>
            mark as favorite
          </span>
        </footer>
      </section>
    </main>

    <script>
      const galleryItems = [
        {
          title: "Soft morning",
          subtitle: "Muted light over the city",
          color: "#0ea5e9",
          image:
            "https://images.pexels.com/photos/34088/pexels-photo.jpg?auto=compress&cs=tinysrgb&w=800",
        },
        {
          title: "Quiet desk",
          subtitle: "Where ideas stay simple",
          color: "#22c55e",
          image:
            "https://images.pexels.com/photos/3746311/pexels-photo-3746311.jpeg?auto=compress&cs=tinysrgb&w=800",
        },
        {
          title: "Empty streets",
          subtitle: "A pause between moments",
          color: "#f97316",
          image:
            "https://images.pexels.com/photos/2406770/pexels-photo-2406770.jpeg?auto=compress&cs=tinysrgb&w=800",
        },
        {
          title: "Soft plant",
          subtitle: "Green against a white wall",
          color: "#a855f7",
          image:
            "https://images.pexels.com/photos/3952025/pexels-photo-3952025.jpeg?auto=compress&cs=tinysrgb&w=800",
        },
        {
          title: "Window light",
          subtitle: "Lines and shadows only",
          color: "#facc15",
          image:
            "https://images.pexels.com/photos/37347/office-freelancer-computer-business-37347.jpeg?auto=compress&cs=tinysrgb&w=800",
        },
        {
          title: "Muted blue",
          subtitle: "A frame within a frame",
          color: "#38bdf8",
          image:
            "https://images.pexels.com/photos/2929224/pexels-photo-2929224.jpeg?auto=compress&cs=tinysrgb&w=800",
        },
      ];

      const tabLogin = document.getElementById("tabLogin");
      const tabSignup = document.getElementById("tabSignup");
      const authTitle = document.getElementById("authTitle");
      const authSubtitle = document.getElementById("authSubtitle");
      const nameField = document.getElementById("nameField");
      const authForm = document.getElementById("authForm");
      const authButtonText = document.getElementById("authButtonText");
      const switchLink = document.getElementById("switchLink");
      const authError = document.getElementById("authError");
      const authErrorText = document.getElementById("authErrorText");
      const nameInput = document.getElementById("nameInput");
      const emailInput = document.getElementById("emailInput");
      const passwordInput = document.getElementById("passwordInput");
      const rememberInput = document.getElementById("rememberInput");
      const userChip = document.getElementById("userChip");
      const userNameEl = document.getElementById("userName");
      const userAvatar = document.getElementById("userAvatar");
      const logoutButton = document.getElementById("logoutButton");
      const galleryGrid = document.getElementById("galleryGrid");

      let currentMode = "login";

      function setMode(mode) {
        currentMode = mode;
        const isLogin = mode === "login";

        tabLogin.classList.toggle("active", isLogin);
        tabSignup.classList.toggle("active", !isLogin);
        tabLogin.setAttribute("aria-pressed", String(isLogin));
        tabSignup.setAttribute("aria-pressed", String(!isLogin));

        if (isLogin) {
          authTitle.textContent = "Welcome back";
          authSubtitle.textContent = "Enter your details to continue.";
          nameField.style.display = "none";
          switchLink.textContent = "New here? Sign up";
          authButtonText.textContent = "Enter gallery";
        } else {
          authTitle.textContent = "Create a calm space";
          authSubtitle.textContent =
            "Sign up with just a name, email, and password.";
          nameField.style.display = "flex";
          switchLink.textContent = "Already have an account? Log in";
          authButtonText.textContent = "Create account";
        }

        hideError();
      }

      function showError(message) {
        authErrorText.textContent = message;
        authError.classList.add("visible");
      }

      function hideError() {
        authError.classList.remove("visible");
        authErrorText.textContent = "";
      }

      function initialsFromName(name) {
        if (!name) return "M";
        const parts = name.trim().split(" ").filter(Boolean);
        if (!parts.length) return "M";
        const first = parts[0][0] || "";
        const second = parts[1] ? parts[1][0] : "";
        return (first + second).toUpperCase();
      }

      function enterGallery(user) {
        const displayName = user.name || user.email || "Guest";
        userNameEl.textContent = displayName;
        userAvatar.textContent = initialsFromName(displayName);
        userChip.style.display = "flex";

        const payload = {
          name: user.name || "",
          email: user.email || "",
          remember: !!user.remember,
        };

        if (payload.remember) {
          localStorage.setItem("minimal-gallery-user", JSON.stringify(payload));
        } else {
          localStorage.removeItem("minimal-gallery-user");
        }

        document.querySelector(".auth-card").style.opacity = "0.85";
      }

      function logout() {
        userChip.style.display = "none";
        localStorage.removeItem("minimal-gallery-user");
        document.querySelector(".auth-card").style.opacity = "1";
      }

      function loadPersistedUser() {
        try {
          const raw = localStorage.getItem("minimal-gallery-user");
          if (!raw) return;
          const data = JSON.parse(raw);
          if (data && data.email) {
            emailInput.value = data.email;
            nameInput.value = data.name || "";
            rememberInput.checked = !!data.remember;
            enterGallery(data);
          }
        } catch (e) {
          console.warn("Could not read stored user", e);
        }
      }

      tabLogin.addEventListener("click", () => setMode("login"));
      tabSignup.addEventListener("click", () => setMode("signup"));

      switchLink.addEventListener("click", () => {
        setMode(currentMode === "login" ? "signup" : "login");
      });

      authForm.addEventListener("submit", (event) => {
        event.preventDefault();
        hideError();

        const email = emailInput.value.trim();
        const password = passwordInput.value;
        const name = nameInput.value.trim();
        const remember = rememberInput.checked;

        if (!email || !password) {
          showError("Please fill in email and password.");
          return;
        }

        if (password.length < 6) {
          showError("Password should be at least 6 characters.");
          return;
        }

        if (currentMode === "signup" && !name) {
          showError("Add a simple name so we know it's you.");
          return;
        }

        enterGallery({ name, email, remember });
      });

      logoutButton.addEventListener("click", () => {
        logout();
      });

      function createGalleryCard(item, index) {
        const card = document.createElement("article");
        card.className = "photo-card";
        card.setAttribute("tabindex", "0");
        card.setAttribute("data-index", String(index));
        card.setAttribute("aria-pressed", "false");

        const media = document.createElement("div");
        media.className = "photo-media";
        const img = document.createElement("img");
        img.src = item.image;
        img.alt = item.title;
        media.appendChild(img);

        const overlay = document.createElement("div");
        overlay.className = "photo-overlay";
        media.appendChild(overlay);

        const footer = document.createElement("div");
        footer.className = "photo-footer";

        const meta = document.createElement("div");
        meta.className = "photo-meta";
        const title = document.createElement("div");
        title.className = "photo-title";
        title.textContent = item.title;
        const subtitle = document.createElement("div");
        subtitle.className = "photo-subtitle";
        subtitle.textContent = item.subtitle;
        meta.appendChild(title);
        meta.appendChild(subtitle);

        const actions = document.createElement("div");
        actions.className = "photo-actions";

        const chip = document.createElement("div");
        chip.className = "chip";
        const chipDot = document.createElement("span");
        chipDot.className = "chip-dot green";
        chipDot.style.background = item.color;
        const chipText = document.createElement("span");
        chipText.textContent = "minimal";
        chip.appendChild(chipDot);
        chip.appendChild(chipText);

        const like = document.createElement("button");
        like.className = "like-button";
        like.type = "button";
        like.innerHTML = "♡";
        like.setAttribute("aria-label", "Mark as favorite");

        actions.appendChild(chip);
        actions.appendChild(like);

        footer.appendChild(meta);
        footer.appendChild(actions);

        card.appendChild(media);
        card.appendChild(footer);

        let liked = false;

        function toggleLike() {
          liked = !liked;
          like.classList.toggle("liked", liked);
          like.innerHTML = liked ? "♥" : "♡";
          card.setAttribute("aria-pressed", String(liked));
        }

        like.addEventListener("click", (event) => {
          event.stopPropagation();
          toggleLike();
        });

        card.addEventListener("click", toggleLike);

        card.addEventListener("keydown", (event) => {
          if (event.key === "Enter" || event.key === " ") {
            event.preventDefault();
            toggleLike();
          }
        });

        return card;
      }

      function populateGallery() {
        galleryGrid.innerHTML = "";
        galleryItems.forEach((item, index) => {
          const card = createGalleryCard(item, index);
          galleryGrid.appendChild(card);
        });
      }

      populateGallery();
      loadPersistedUser();
    </script>
  </body>
</html>
