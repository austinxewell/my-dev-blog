---
layout: home
title: "Hi, I'm Austin 👋"
---

<div class="hero">
  <img 
    src="{{ "/assets/images/auewellify_avi.png" | relative_url }}" 
    alt="Austin avatar"
  />
  <div class="hero-content">
    <h2>Frontend Engineer | Nuxt & TypeScript</h2>
    <p>
        I’m a <strong>Frontend Engineer</strong> focused on building <strong>scalable, maintainable, and user-friendly web applications</strong>. I specialize in <strong>Nuxt, TypeScript, Vue, and modern frontend architectures</strong>, and I enjoy translating complex design and product requirements into seamless user experiences.
    </p>
  </div>
</div>

---

## 🚀 Some of The Projects I’ve Worked on Include

<div class="projects">

<div class="project">
<strong>Planning Poker</strong><br>
Collaborative Agile estimation platform built with Nuxt 3 + TypeScript.  
It supports live voting and real-time team planning rooms.
</div>

<div class="project">
<strong>Nuxt ESLint Automation Script</strong><br>
CLI tool that automates ESLint setup for Nuxt projects, improving developer workflow and code consistency.
</div>

<div class="project">
<strong>Git-N-Shape</strong><br>
 A fitness tracking app that supports multiple users, team challenges, and shared data, showcasing collaborative features and team development.
</div>

</div>

---

## 🛠️ A Quick Look At My Common Tech Stack

<div class="tech-grid">

<div>
<strong>Frontend</strong>
<ul>
<li>Vue</li>
<li>Nuxt (v2–v4, Composition API)</li>
<li>React</li>
<li>Vite</li>
</ul>
</div>

<div>
<strong>Languages & Frameworks</strong>
<ul>
<li>JavaScript / TypeScript</li>
<li>PHP</li>
<li>HTML / CSS / SASS</li>
<li>BEM / Tailwind</li>
</ul>
</div>

<div>
<strong>Backend & Data</strong>
<ul>
<li>Node.js / Express</li>
<li>GraphQL / REST</li>
<li>SQL / NoSQL</li>
<li>Firebase / Supabase</li>
</ul>
</div>

<div>
<strong>Workflow & Testing</strong>
<ul>
<li>Agile / Scrum</li>
<li>CI/CD</li>
<li>OOP / MVC</li>
<li>Cypress / Jest</li>
</ul>
</div>

</div>
<br>

---

<style>
.hero {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 3rem;
  margin: 3rem 0;
  max-width: 900px;
}

.hero img {
  width: 200px;
  border-radius: 50%;
  flex-shrink: 0;
}

.hero-content {
  max-width: 600px;
}

.hero-content h2 {
  margin-top: 0;
  margin-bottom: 0.75rem;
}

@media (max-width: 768px) {
  .hero {
    flex-direction: column;
    text-align: center;
  }

  .hero-content {
    max-width: 100%;
  }
}

.projects {
  margin: 2rem 0;
}

.project {
  margin-bottom: 1.5rem;
}

.tech-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1.5rem;
  margin-top: 1rem;
}

/* Stack on smaller screens */
@media (max-width: 700px) {
  .tech-grid {
    grid-template-columns: 1fr;
  }
}

.tech-grid > div {
  padding: 1rem;
  border: 1px solid rgba(0,0,0,0.08);
  border-radius: 12px;
}

.tech-grid ul {
  margin: 0.5rem 0 0;
  padding-left: 1.1rem;
}
</style>
