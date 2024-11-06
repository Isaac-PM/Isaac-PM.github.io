<style>
  #header {
    display: none !important;
  }

  section {
    margin-top: 0 !important;
    max-width: 800px !important;
  }

  .wrapper {
    max-width: 800px !important;
  }

  .job-container {
    display: flex;
    align-items: center;
    background-color: #333;
    padding: 20px;
    margin: 20px 0;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
    transition: transform 0.3s ease;
  }

  .job-image img {
    width: 200px;
    height: 120px;
    object-fit: cover;
    border-radius: 5px;
    margin-right: 20px;
    border: 3px solid #f0f0f0;
  }

  .job-description h2 {
    margin: 0;
    color: #c0c0c0;
    font-size: 1.5em;
  }

  .job-description p {
    margin: 5px 0;
    color: #e0e0e0;
    font-size: 0.9em;
    line-height: 1.4;
  }

  .job-description p strong {
    color: #a8a8a8;
  }

  .job-institution {
    font-style: italic;
  }

  .button-midnight {
    background-color: #444;
    color: #fff;
    border: 1px solid #666;
    padding: 8px 16px;
    border-radius: 5px;
    text-transform: uppercase;
    font-weight: bold;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s, border-color 0.3s;
    font-size: 0.9em;
  }

  .button-midnight:hover {
    background-color: #666;
    color: #fff;
    border-color: #888;
  }

  .button-midnight:active {
    background-color: #333;
    color: #fff;
    border-color: #555;
  }
</style>

# Current work

<div id="jobs"></div>

# Get to know me better

- [Curriculum Vitae]()
- [LinkedIn]()
- [GitHub]

<small>
Last updated: 2024-11-06
</small>

<script>
  class Job {
    constructor(title, institution, location, description, link, linkTitle) {
      this.title = title;
      this.location = location;
      this.description = description;
      this.link = link;
      this.linkTitle = linkTitle;
    }
  }

  function jobContainer(job) {
    return `
      <div class="job-container">
        <div class="job-description">
          <h2>${job.title}</h2>
          <p class="job-institution">${job.institution}</p>
          <p>${job.location}</p>
          <p>${job.description}</p>
          <a href="${job.link}" target="_blank">
            <button class="button-midnight">${job.linkTitle}</button>
          </a>
        </div>
      </div>
    `;
  }

  fetch("jobs.json")
    .then((response) => response.json())
    .then((jobs) => {
      document.getElementById("jobs").innerHTML = jobs.map(jobContainer).join("");
    })
    .catch((error) => console.error("Error loading jobs:", error));
</script>
