#!/bin/bash
# Fetch dad jokes and update the HTML page

API_URL="https://icanhazdadjoke.com/"
HTML_FILE="/html/index.html"

echo "Starting joke updater..."

while true; do
  # Fetch a random dad joke
  JOKE=$(curl -s "$API_URL" -H "Accept: text/plain")

  # Generate HTML
  cat > "$HTML_FILE" << EOF
<!DOCTYPE html>
<html>
<head>
  <title>Dad Joke Dashboard</title>
  <style>
    body {
      font-family: sans-serif;
      max-width: 600px;
      margin: 50px auto;
      padding: 20px;
      text-align: center;
    }
    .joke {
      font-size: 1.5em;
      margin: 40px 0;
      padding: 20px;
      background: #f0f0f0;
      border-radius: 10px;
    }
    .meta {
      color: #666;
      font-size: 0.9em;
    }
  </style>
</head>
<body>
  <h1>Dad Joke Dashboard</h1>
  <div class="joke">$JOKE</div>
  <p class="meta">Updated: $(date)</p>
  <p class="meta">Refreshes every 30 seconds</p>
</body>
</html>
EOF

  echo "Updated joke: $JOKE"
  sleep 30
done
