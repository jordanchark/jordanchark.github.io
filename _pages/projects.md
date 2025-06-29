---
layout: default
title: projects
nav: true
nav_order: 3
permalink: /projects/
---

<div class="projects">
  {% assign ongoing_projects = site.project_items | where: "status", "ongoing" | sort: "start_date" | reverse %}
  {% assign completed_projects = site.project_items | where: "status", "completed" | sort: "start_date" | reverse %}
  
  <h1 class="page-title">Research Projects</h1>
  
  {% if ongoing_projects.size > 0 %}
    <div class="section-header">
      <h2 class="section-title">Ongoing Projects</h2>
      <div class="status-dot ongoing"></div>
    </div>
    
    <div class="projects-list">
      {% for project in ongoing_projects %}
        <article class="project ongoing">
          <header class="project-header">
            <h3 class="project-title">{{ project.title }}</h3>
            <span class="project-duration">{{ project.start_date | date: "%b %Y" }} - Present</span>
          </header>
          
          {% if project.collaborators %}
            <div class="project-meta">
              <div class="collaborators-label">Collaborators</div>
              <div class="collaborators-list">
                {% for collab in project.collaborators %}
                  <div class="collaborator">
                    <span class="collaborator-name">{{ collab.name }}</span>
                    <span class="collaborator-affiliation">{{ collab.affiliation }}</span>
                  </div>
                {% endfor %}
              </div>
            </div>
          {% endif %}
          
          <div class="project-description">
            {{ project.content }}
          </div>
          
          {% if project.links %}
            <div class="project-links">
              {% for link in project.links %}
                <a href="{{ link.url }}" class="project-link">{{ link.text }}</a>
              {% endfor %}
            </div>
          {% endif %}
          
          {% if project.papers or project.presentations %}
            <div class="citations-section">
              {% if project.papers %}
                <div class="citation-category">
                  <div class="citation-label">Papers</div>
                  <ul class="citation-list">
                    {% for paper in project.papers %}
                      <li class="citation-item">
                        <div class="citation-text">
                          {{ paper.citation }}
                          {% if paper.journal %}
                            <a href="{{ paper.url }}" class="citation-link"><em>{{ paper.journal }}</em>{% if paper.volume %}, {{ paper.volume }}{% endif %}{% if paper.pages %}, {{ paper.pages }}{% endif %}</a>.
                          {% else %}
                            <a href="{{ paper.url }}" class="citation-link"><em>{{ paper.journal }}</em></a>.
                          {% endif %}
                        </div>
                      </li>
                    {% endfor %}
                  </ul>
                </div>
              {% endif %}
              
              {% if project.presentations %}
                <div class="citation-category">
                  <div class="citation-label">Presentations</div>
                  <ul class="citation-list">
                    {% for presentation in project.presentations %}
                      <li class="citation-item">
                        <div class="citation-text">
                          <a href="{{ presentation.url }}" class="citation-link">{{ presentation.citation }}</a>
                          {{ presentation.venue }}.
                        </div>
                      </li>
                    {% endfor %}
                  </ul>
                </div>
              {% endif %}
            </div>
          {% endif %}
        </article>
      {% endfor %}
    </div>
  {% endif %}
  
  {% if completed_projects.size > 0 %}
    <div class="section-header">
      <h2 class="section-title">Completed Projects</h2>
      <div class="status-dot completed"></div>
    </div>
    
    <div class="projects-list">
      {% for project in completed_projects %}
        <article class="project completed">
          <header class="project-header">
            <h3 class="project-title">{{ project.title }}</h3>
            <span class="project-duration">{{ project.start_date | date: "%b %Y" }} - {{ project.end_date | date: "%b %Y" }}</span>
          </header>
          
          {% if project.collaborators %}
            <div class="project-meta">
              <div class="collaborators-label">Collaborators</div>
              <div class="collaborators-list">
                {% for collab in project.collaborators %}
                  <div class="collaborator">
                    <span class="collaborator-name">{{ collab.name }}</span>
                    <span class="collaborator-affiliation">{{ collab.affiliation }}</span>
                  </div>
                {% endfor %}
              </div>
            </div>
          {% endif %}
          
          <div class="project-description">
            {{ project.content }}
          </div>
          
          {% if project.links %}
            <div class="project-links">
              {% for link in project.links %}
                <a href="{{ link.url }}" class="project-link">{{ link.text }}</a>
              {% endfor %}
            </div>
          {% endif %}
          
          {% if project.papers or project.presentations %}
            <div class="citations-section">
              {% if project.papers %}
                <div class="citation-category">
                  <div class="citation-label">Papers</div>
                  <ul class="citation-list">
                    {% for paper in project.papers %}
                      <li class="citation-item">
                        <div class="citation-text">
                          {{ paper.citation }}
                          {% if paper.journal %}
                            <a href="{{ paper.url }}" class="citation-link"><em>{{ paper.journal }}</em>{% if paper.volume %}, {{ paper.volume }}{% endif %}{% if paper.pages %}, {{ paper.pages }}{% endif %}</a>.
                          {% else %}
                            <a href="{{ paper.url }}" class="citation-link"><em>{{ paper.journal }}</em></a>.
                          {% endif %}
                        </div>
                      </li>
                    {% endfor %}
                  </ul>
                </div>
              {% endif %}
              
              {% if project.presentations %}
                <div class="citation-category">
                  <div class="citation-label">Presentations</div>
                  <ul class="citation-list">
                    {% for presentation in project.presentations %}
                      <li class="citation-item">
                        <div class="citation-text">
                          <a href="{{ presentation.url }}" class="citation-link">{{ presentation.citation }}</a>
                          {{ presentation.venue }}.
                        </div>
                      </li>
                    {% endfor %}
                  </ul>
                </div>
              {% endif %}
            </div>
          {% endif %}
        </article>
      {% endfor %}
    </div>
  {% endif %}
</div>