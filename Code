<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Document Storage Decision Tree</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 2em; max-width: 600px; }
    button { margin-top: 1em; margin-right: 10px; }
    .question, .result { margin-top: 2em; }
  </style>
</head>
<body>
  <h1>Where Should I Save This Document?</h1>
  <div id="content"></div>

  <script>
    const questions = [
      {
        text: "Does this document contain sensitive content such as payroll information, HR files, or other restricted content?",
        yes: "dropboxSensitive",
        no: 1
      },
      {
        text: "Is this document currently being edited, in the draft phase, or a work in progress?",
        yes: "googleDriveWork",
        no: 2
      },
      {
        text: "Is this document an important legal or financial document, or needed for official record-keeping?",
        yes: "dropboxOfficial",
        no: "googleDriveFinal"
      }
    ];

    const results = {
      dropboxSensitive: {
        title: "Save in Dropbox",
        desc: "Sensitive content should be stored in Dropbox. Examples: payroll, HR files, audits."
      },
      googleDriveWork: {
        title: "Save in Google Drive",
        desc: "Work-in-progress documents go in Google Drive. Examples: drafts, proposals, presentations."
      },
      dropboxOfficial: {
        title: "Save in Dropbox",
        desc: "Final official documents go in Dropbox. Examples: legal files, final budgets, SOPs."
      },
      googleDriveFinal: {
        title: "Save in Google Drive",
        desc: "Final but non-official documents go in Google Drive. Examples: final slide decks, blogs, internal plans."
      }
    };

    let step = 0;

    function showQuestion(index) {
      const question = questions[index];
      const container = document.getElementById("content");
      container.innerHTML = `
        <div class="question">
          <h2>${question.text}</h2>
          <button onclick="handleAnswer('yes')">Yes</button>
          <button onclick="handleAnswer('no')">No</button>
        </div>
      `;
    }

    function handleAnswer(answer) {
      const next = questions[step][answer];
      if (typeof next === "string") {
        showResult(next);
      } else {
        step = next;
        showQuestion(step);
      }
    }

    function showResult(key) {
      const result = results[key];
      const container = document.getElementById("content");
      container.innerHTML = `
        <div class="result">
          <h2>${result.title}</h2>
          <p>${result.desc}</p>
          <button onclick="restart()">Start Over</button>
        </div>
      `;
    }

    function restart() {
      step = 0;
      showQuestion(step);
    }

    // Start app
    showQuestion(step);
  </script>
</body>
</html>
