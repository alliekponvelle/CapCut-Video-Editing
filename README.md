<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CapCut Video Editing</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@600;700&family=Manrope:wght@400;500;700;800&display=swap" rel="stylesheet">
  <style>
    :root {
      --panel: rgba(248, 239, 221, 0.96);
      --panel-soft: rgba(255, 248, 234, 0.86);
      --text: #2e1a40;
      --muted: #66507b;
      --purple: #71419b;
      --purple-deep: #29123f;
      --gold: #d7b15c;
      --red: #b43b4d;
      --green: #368856;
      --line: rgba(113, 65, 155, 0.15);
      --shadow: 0 24px 60px rgba(8, 2, 15, 0.35);
      --radius: 28px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }

    body {
      margin: 0;
      font-family: "Manrope", sans-serif;
      background:
        radial-gradient(circle at top left, rgba(215, 177, 92, 0.12), transparent 22%),
        radial-gradient(circle at 85% 15%, rgba(113, 65, 155, 0.24), transparent 24%),
        linear-gradient(160deg, #0f0618 0%, #1c0c2c 38%, #30124b 72%, #12081d 100%);
      color: #f9f0dc;
      line-height: 1.6;
      min-height: 100vh;
    }

    .page {
      width: min(1180px, calc(100% - 32px));
      margin: 0 auto;
      padding: 28px 0 56px;
    }

    .hero {
      position: relative;
      overflow: hidden;
      padding: 56px 42px;
      border-radius: 0 0 34px 34px;
      background: linear-gradient(140deg, #160920 0%, #341552 34%, #71419b 70%, #d7b15c 100%);
      box-shadow: var(--shadow);
      isolation: isolate;
    }

    .hero::before,
    .hero::after {
      content: "";
      position: absolute;
      border-radius: 50%;
      background: rgba(255,255,255,0.08);
      filter: blur(2px);
      z-index: -1;
    }

    .hero::before {
      width: 260px;
      height: 260px;
      top: -100px;
      right: -60px;
    }

    .hero::after {
      width: 180px;
      height: 180px;
      bottom: -60px;
      left: 10px;
    }

    .eyebrow,
    .section-label,
    .pill {
      display: inline-flex;
      align-items: center;
      padding: 7px 14px;
      border-radius: 999px;
      font-size: 11px;
      font-weight: 800;
      letter-spacing: 0.12em;
      text-transform: uppercase;
    }

    .eyebrow {
      background: rgba(255,255,255,0.14);
      border: 1px solid rgba(255,255,255,0.22);
      color: #fff5dd;
    }

    .section-label {
      background: rgba(215, 177, 92, 0.16);
      color: var(--purple);
      margin-bottom: 14px;
    }

    .pill {
      background: rgba(113, 65, 155, 0.1);
      color: var(--purple-deep);
      margin: 0 6px 8px 0;
      letter-spacing: 0.08em;
    }

    h1, h2, h3 {
      margin: 0;
      font-family: "Cinzel", serif;
      font-weight: 700;
      letter-spacing: 0.02em;
    }

    h1 {
      margin-top: 18px;
      font-size: clamp(2.6rem, 7vw, 5rem);
      line-height: 0.96;
      max-width: 11ch;
    }

    .hero p {
      max-width: 72ch;
      margin: 18px 0 0;
      font-size: 1.04rem;
      color: rgba(255, 248, 235, 0.92);
    }

    .hero-grid,
    .grid-2,
    .grid-3,
    .grid-4 {
      display: grid;
      gap: 16px;
      margin-top: 18px;
    }

    .hero-grid {
      grid-template-columns: repeat(4, minmax(0, 1fr));
      margin-top: 28px;
    }

    .grid-2 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
    .grid-3 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
    .grid-4 { grid-template-columns: repeat(4, minmax(0, 1fr)); }

    .hero-stat {
      padding: 16px;
      border-radius: 18px;
      background: rgba(255,255,255,0.12);
      border: 1px solid rgba(255,255,255,0.16);
      backdrop-filter: blur(8px);
    }

    .hero-stat strong {
      display: block;
      font-size: 1.2rem;
      margin-bottom: 4px;
      color: #fff5dd;
    }

    .section,
    .cta {
      margin-top: 18px;
      padding: 28px;
      background: var(--panel);
      color: var(--text);
      box-shadow: var(--shadow);
      border-radius: var(--radius);
      border: 1px solid rgba(255,255,255,0.28);
    }

    .section h2 {
      font-size: clamp(1.8rem, 4vw, 2.7rem);
      line-height: 1.02;
      margin-bottom: 12px;
    }

    .section p {
      margin: 0 0 14px;
      color: var(--muted);
    }

    .card,
    .lesson-card,
    .template-card,
    .warning-card {
      background: var(--panel-soft);
      border: 1px solid var(--line);
      border-radius: 22px;
      padding: 18px;
    }

    .lesson-card { border-top: 4px solid var(--purple); }
    .warning-card { border-top: 4px solid var(--red); }
    .template-card { border-top: 4px solid var(--green); }

    .card h3,
    .lesson-card h3,
    .template-card h3,
    .warning-card h3 {
      font-size: 1.08rem;
      color: var(--purple-deep);
      margin-bottom: 8px;
    }

    ul,
    ol {
      margin: 0;
      padding-left: 20px;
      color: var(--muted);
    }

    li { margin-bottom: 8px; }

    code,
    pre {
      font-family: Consolas, "Courier New", monospace;
    }

    pre {
      white-space: pre-wrap;
      margin: 12px 0 0;
      padding: 14px;
      border-radius: 16px;
      background: rgba(41, 18, 63, 0.08);
      border: 1px solid rgba(113, 65, 155, 0.12);
      color: var(--purple-deep);
      font-weight: 700;
    }

    a {
      color: var(--purple-deep);
      font-weight: 800;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 18px;
      overflow: hidden;
      border-radius: 18px;
      background: rgba(255, 248, 234, 0.72);
    }

    th,
    td {
      padding: 13px 14px;
      text-align: left;
      border-bottom: 1px solid var(--line);
      vertical-align: top;
      color: var(--muted);
      font-size: 0.95rem;
    }

    th {
      color: var(--purple-deep);
      background: rgba(215, 177, 92, 0.18);
      font-weight: 800;
    }

    tr:last-child td { border-bottom: 0; }

    .quote {
      padding: 18px;
      margin-top: 18px;
      border-radius: 22px;
      background: linear-gradient(135deg, rgba(215, 177, 92, 0.18), rgba(113, 65, 155, 0.08));
      border: 1px solid rgba(215, 177, 92, 0.22);
      color: var(--purple-deep);
      font-weight: 700;
    }

    .cta {
      text-align: center;
      background: linear-gradient(135deg, rgba(41, 18, 63, 0.98), rgba(113, 65, 155, 0.92));
      color: #fff4de;
    }

    .cta h2 {
      font-size: clamp(1.9rem, 4vw, 3rem);
      margin-bottom: 12px;
    }

    .cta p {
      max-width: 66ch;
      margin: 0 auto;
      color: rgba(255, 243, 221, 0.88);
    }

    @media (max-width: 980px) {
      .hero-grid,
      .grid-2,
      .grid-3,
      .grid-4 {
        grid-template-columns: 1fr;
      }

      table,
      thead,
      tbody,
      th,
      td,
      tr {
        display: block;
      }

      th { display: none; }

      td {
        border-bottom: 0;
        padding: 10px 14px;
      }

      tr {
        border-bottom: 1px solid var(--line);
        padding: 8px 0;
      }
    }

    @media (max-width: 640px) {
      .page {
        width: min(100% - 16px, 1180px);
      }

      .hero,
      .section,
      .cta {
        padding: 22px;
      }
    }
  </style>
</head>
<body>
  <div class="page">
    <section class="hero">
      <span class="eyebrow">Module 8</span>
      <h1>CapCut Video Editing</h1>
      <p>Learn how to turn rough video clips into clean short-form content with hooks, trims, captions, B-roll, overlays, sound, pacing, and exports that are ready for TikTok, Reels, Shorts, and product promotion.</p>
      <div class="hero-grid">
        <div class="hero-stat">
          <strong>Hook</strong>
          <span>Get attention in the first seconds with stronger openings</span>
        </div>
        <div class="hero-stat">
          <strong>Edit</strong>
          <span>Trim clips, remove dead space, add B-roll, and improve pacing</span>
        </div>
        <div class="hero-stat">
          <strong>Caption</strong>
          <span>Use on-screen text and captions to improve clarity and watch time</span>
        </div>
        <div class="hero-stat">
          <strong>Export</strong>
          <span>Send out clean videos in the right format for each platform</span>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Why It Matters</div>
      <h2>Editing Makes the Message Easier to Watch</h2>
      <p>Good editing is not about making everything flashy. It is about helping people follow the message, stay engaged, and understand the next step. Clean edits usually outperform complicated edits when the offer and message are clear.</p>
      <div class="quote">The goal is not to edit forever. The goal is to edit fast enough to stay consistent and clean enough to hold attention.</div>
    </section>

    <section class="section">
      <div class="section-label">Module Promise</div>
      <h2>What Students Will Learn</h2>
      <div class="grid-3">
        <div class="card">
          <h3>CapCut Basics</h3>
          <p>Students learn the editor layout, timeline, clips, tracks, text, audio, exports, and project flow.</p>
        </div>
        <div class="card">
          <h3>Stronger Hooks</h3>
          <p>Students learn how to open videos faster with clear first lines, on-screen text, and visual movement.</p>
        </div>
        <div class="card">
          <h3>Trimming and Pacing</h3>
          <p>Students learn how to remove silence, tighten scenes, and improve energy without making the video feel chaotic.</p>
        </div>
        <div class="card">
          <h3>Captions and Text</h3>
          <p>Students learn how to use readable captions and text overlays that support the message.</p>
        </div>
        <div class="card">
          <h3>B-Roll and Overlays</h3>
          <p>Students learn how to add extra visuals, product shots, screenshots, and supporting clips.</p>
        </div>
        <div class="card">
          <h3>Exports and Reuse</h3>
          <p>Students learn how to export, repurpose, and reuse video formats for TikTok, Reels, Shorts, and ads.</p>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Lesson Plan</div>
      <h2>Full Module Outline</h2>
      <div class="grid-2">
        <div class="lesson-card">
          <span class="pill">Lesson 1</span>
          <h3>CapCut Basics and Project Setup</h3>
          <p>Students should understand the editor before trying to make a polished video. CapCut becomes easier once students know where the timeline, clips, text tools, audio, stickers, effects, and export settings live.</p>
          <ul>
            <li>Create a new project and import clips.</li>
            <li>Understand the timeline and how clip order changes the story.</li>
            <li>Use the preview window to watch the edit as it develops.</li>
            <li>Rename projects clearly so they are easy to find later.</li>
            <li>Duplicate projects before making major changes.</li>
          </ul>
          <div class="quote">Student task: create one CapCut project using 3 short clips and one piece of text.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 2</span>
          <h3>Editing the Hook</h3>
          <p>The first 1 to 3 seconds matter most. Students should give the viewer a reason to keep watching immediately.</p>
          <ul>
            <li>Open with a strong line, bold caption, or surprising statement.</li>
            <li>Start after the hesitation, not before it.</li>
            <li>Use movement in the first shot if possible.</li>
            <li>Cut out "hey guys" or long intros if they weaken the opening.</li>
            <li>Match the hook text to what the video actually delivers.</li>
          </ul>
          <div class="quote">Hook rule: the first line should name the problem, the promise, or the curiosity.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 3</span>
          <h3>Trimming and Removing Dead Space</h3>
          <p>Dead space makes videos feel slower than they are. Students should learn how to cut silence, remove repeated thoughts, and tighten the message without making it hard to understand.</p>
          <ul>
            <li>Trim before and after every spoken line when needed.</li>
            <li>Cut filler words if they slow the video down.</li>
            <li>Keep breathing room where clarity matters.</li>
            <li>Use jump cuts carefully so the edit still feels intentional.</li>
            <li>Watch the whole edit once just for pacing.</li>
          </ul>
          <div class="quote">Editing question: if this second disappeared, would the message still work?</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 4</span>
          <h3>Captions and On-Screen Text</h3>
          <p>Captions help people follow the video even when they are watching without sound. On-screen text also helps highlight the main point.</p>
          <ul>
            <li>Use auto captions, then clean them up manually.</li>
            <li>Keep caption styles readable and consistent.</li>
            <li>Do not place text where platform buttons will cover it.</li>
            <li>Highlight keywords when it helps the message.</li>
            <li>Keep the text large enough for phones.</li>
          </ul>
          <div class="quote">Caption rule: readability matters more than fancy styling.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 5</span>
          <h3>B-Roll, Product Clips, and Overlays</h3>
          <p>B-roll gives the viewer something to look at while the speaker explains the point. It also helps product-based videos feel more real.</p>
          <ul>
            <li>Use screenshots, website recordings, store pages, product mockups, or phone demos.</li>
            <li>Show what the speaker is talking about, not random filler clips.</li>
            <li>Use overlays to support the explanation, not distract from it.</li>
            <li>Keep transitions simple if the clip already says enough.</li>
            <li>Use zoom or crop to direct attention to the right place.</li>
          </ul>
          <div class="quote">B-roll rule: every extra visual should answer, "What should the viewer look at right now?"</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 6</span>
          <h3>Audio, Music, and Voice Balance</h3>
          <p>Students should keep voice clarity first. Background music should support the energy of the video without overpowering the message.</p>
          <ul>
            <li>Keep voice volume clear and consistent.</li>
            <li>Lower music under voiceovers and speaking clips.</li>
            <li>Use music that matches the mood and speed of the content.</li>
            <li>Avoid harsh sound changes between clips.</li>
            <li>Use simple sound effects only when they support the edit.</li>
          </ul>
          <div class="quote">Audio rule: if the viewer cannot hear the message clearly, the edit is not done yet.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 7</span>
          <h3>Transitions, Zooms, and Effects</h3>
          <p>Effects can improve energy, but too many effects can make a video look amateur. Students should use simple movement that supports the message.</p>
          <ul>
            <li>Use transitions only when clips need smoother movement.</li>
            <li>Use zoom for emphasis, not every second.</li>
            <li>Use effects sparingly so the content stays clear.</li>
            <li>Keep one visual style per video when possible.</li>
            <li>Avoid editing tricks that distract from the offer.</li>
          </ul>
          <div class="quote">Editing rule: if the effect is more noticeable than the message, it is probably too much.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 8</span>
          <h3>Talking Head Videos</h3>
          <p>Talking head videos are one of the fastest ways to build trust. Students should learn how to keep these videos visually active without overediting.</p>
          <ul>
            <li>Use jump cuts to remove pauses.</li>
            <li>Add text hooks and caption highlights.</li>
            <li>Add B-roll where explanation needs proof.</li>
            <li>Use close-up crop changes sparingly for energy.</li>
            <li>Keep the face bright and centered.</li>
          </ul>
          <div class="quote">Simple talking head formula: hook, problem, one tip, next step.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 9</span>
          <h3>Product and Tutorial Videos</h3>
          <p>Students can also use CapCut for screen recordings, product explainers, walkthroughs, before-and-after examples, and visual demonstrations.</p>
          <ul>
            <li>Start with the result the viewer wants.</li>
            <li>Show the steps in order.</li>
            <li>Use arrows, crop, and zoom to direct the eye.</li>
            <li>Keep tutorials short and focused on one outcome.</li>
            <li>End with a CTA to the full product, guide, store, or next lesson.</li>
          </ul>
          <div class="quote">Tutorial rule: show the result fast, then explain only what the viewer needs to copy it.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 10</span>
          <h3>Exporting and Repurposing</h3>
          <p>Students should export videos in a format that fits the platform and then reuse the content where it makes sense.</p>
          <ul>
            <li>Use vertical video for TikTok, Reels, and Shorts.</li>
            <li>Check aspect ratio before exporting.</li>
            <li>Review the full video once before export.</li>
            <li>Export with clean file names.</li>
            <li>Repurpose one edit across platforms when the content fits.</li>
            <li>Save project files if the video may need changes later.</li>
          </ul>
          <div class="quote">Repurposing rule: one good short-form video can become a Reel, TikTok, Short, story clip, or ad creative.</div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Video Formula</div>
      <h2>Simple Short-Form Structure</h2>
      <table>
        <thead>
          <tr>
            <th>Part</th>
            <th>What It Should Do</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Hook</td><td>Stop the scroll with a problem, promise, curiosity line, or strong visual.</td></tr>
          <tr><td>Context</td><td>Tell viewers why this matters or who it is for.</td></tr>
          <tr><td>Main Point</td><td>Teach the tip, explain the step, or show the product clearly.</td></tr>
          <tr><td>Visual Support</td><td>Use captions, B-roll, screenshots, overlays, or zoom to support understanding.</td></tr>
          <tr><td>CTA</td><td>Tell viewers what to do next: comment, follow, click, watch, buy, or check the link in bio.</td></tr>
        </tbody>
      </table>
    </section>

    <section class="section">
      <div class="section-label">Templates</div>
      <h2>Swipe Examples</h2>
      <div class="grid-2">
        <div class="template-card">
          <h3>Hook Script</h3>
          <pre>If you are still [problem], this is the part you need to fix first.</pre>
        </div>
        <div class="template-card">
          <h3>Problem-Solution Script</h3>
          <pre>Most people think [wrong idea]. What actually helps is [better approach].</pre>
        </div>
        <div class="template-card">
          <h3>Promo Video Script</h3>
          <pre>If you want help with [problem], I made [offer] to help you [result]. The link is in my bio.</pre>
        </div>
        <div class="template-card">
          <h3>Tutorial Script</h3>
          <pre>Here is how to [result] in three quick steps. Step one... Step two... Step three...</pre>
        </div>
        <div class="template-card">
          <h3>Talking Head CTA</h3>
          <pre>If you want the full checklist, guide, or template, go to the link in my bio.</pre>
        </div>
        <div class="template-card">
          <h3>Editing Notes Template</h3>
          <pre>Hook:
Main point:
B-roll needed:
Caption words to highlight:
CTA:
Platform:
Export name:</pre>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Student Projects</div>
      <h2>What to Create in This Module</h2>
      <div class="grid-3">
        <div class="template-card"><h3>Talking Head Video</h3><p>Create one 20 to 45 second talking head video with a hook, captions, and a CTA.</p></div>
        <div class="template-card"><h3>Product Video</h3><p>Create one short promo video for a digital product, service, or resource.</p></div>
        <div class="template-card"><h3>Screen Tutorial</h3><p>Create one short tutorial with screen recording, zooms, and text guidance.</p></div>
        <div class="template-card"><h3>B-Roll Edit</h3><p>Create one edit using voiceover plus B-roll and screenshots.</p></div>
        <div class="template-card"><h3>Captioned Reel</h3><p>Create one Reel with cleaned captions and keyword highlights.</p></div>
        <div class="template-card"><h3>Repurposed Clip</h3><p>Take one video and adapt it for two different platforms.</p></div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Checklists</div>
      <h2>Student Downloads to Include</h2>
      <div class="grid-2">
        <div class="template-card">
          <h3>Before You Edit Checklist</h3>
          <ol>
            <li>Know the goal of the video.</li>
            <li>Choose the platform first.</li>
            <li>Write the hook before editing.</li>
            <li>Collect clips, screenshots, and B-roll.</li>
            <li>Choose one main CTA.</li>
            <li>Decide whether the video needs captions.</li>
          </ol>
        </div>
        <div class="template-card">
          <h3>Before You Export Checklist</h3>
          <ol>
            <li>Watch the full video once without editing.</li>
            <li>Check spelling in text and captions.</li>
            <li>Make sure voice is clear.</li>
            <li>Make sure captions do not block the face or buttons.</li>
            <li>Check the CTA.</li>
            <li>Export in the right size and format.</li>
          </ol>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Common Mistakes</div>
      <h2>What Students Should Avoid</h2>
      <div class="grid-3">
        <div class="warning-card">
          <h3>Weak First Seconds</h3>
          <p>If the opening does not create curiosity or name the problem, people may leave before the message starts.</p>
        </div>
        <div class="warning-card">
          <h3>Too Many Effects</h3>
          <p>Fancy transitions and effects can make a video look busy instead of strong.</p>
        </div>
        <div class="warning-card">
          <h3>Tiny Captions</h3>
          <p>If captions are too small or too low on the screen, they become hard to use on mobile.</p>
        </div>
        <div class="warning-card">
          <h3>Bad Audio Balance</h3>
          <p>Viewers will leave faster if they cannot hear the voice clearly over the music.</p>
        </div>
        <div class="warning-card">
          <h3>Random B-Roll</h3>
          <p>Every supporting visual should help explain the message, not distract from it.</p>
        </div>
        <div class="warning-card">
          <h3>No CTA</h3>
          <p>If the viewer does not know what to do next, the video may get attention without moving the business forward.</p>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Knowledge Check</div>
      <h2>Quick Student Quiz</h2>
      <div class="grid-2">
        <div class="card">
          <h3>Question 1</h3>
          <p>What is the main job of the first 1 to 3 seconds?</p>
          <div class="quote">Answer: To stop the scroll and give the viewer a reason to keep watching.</div>
        </div>
        <div class="card">
          <h3>Question 2</h3>
          <p>Why should captions be cleaned up after auto captions are created?</p>
          <div class="quote">Answer: Because auto captions can contain mistakes, awkward timing, or unclear wording.</div>
        </div>
        <div class="card">
          <h3>Question 3</h3>
          <p>What should B-roll do?</p>
          <div class="quote">Answer: Support the message by showing what the viewer should pay attention to.</div>
        </div>
        <div class="card">
          <h3>Question 4</h3>
          <p>Should students use every effect CapCut offers?</p>
          <div class="quote">Answer: No. Use only the effects that improve clarity, energy, or flow.</div>
        </div>
      </div>
    </section>

    <section class="cta">
      <h2>Edit for Clarity First</h2>
      <p>CapCut works best when the message is clear, the pacing is clean, the captions are readable, and the CTA gives the viewer a simple next step.</p>
    </section>
  </div>
</body>
</html>
