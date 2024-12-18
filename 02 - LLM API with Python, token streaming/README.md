from flask import Flask, jsonify, request, render_template
import openai
import os

app = Flask(__name__)

# Configure OpenAI API Key
openai.api_key = os.getenv("OPENAI_API_KEY")

# Home Page
@app.route('/')
def home():
    return render_template('index.html')

# API Route: Instructor Profile
@app.route('/api/instructor', methods=['GET'])
def get_instructor():
    instructor_profile = {
        "name": "John Doe",
        "experience": "13+ years in IT, Education, and AI",
        "career_milestones": [
            "Test Automation Engineer",
            "Regional Education Initiatives Leader",
            "AI and ML Expert"
        ]
    }
    return jsonify(instructor_profile)

# API Route: AI Fundamentals
@app.route('/api/fundamentals', methods=['GET'])
def get_fundamentals():
    fundamentals = {
        "AI": "Mimics human behavior using algorithms.",
        "ML": "A subset of AI that learns from data.",
        "Deep Learning": "A subset of ML using neural networks.",
        "NLP": "Processes and analyzes human language."
    }
    return jsonify(fundamentals)

# API Route: Generate Text (GPT API)
@app.route('/api/generate-text', methods=['POST'])
def generate_text():
    data = request.json
    prompt = data.get('prompt', '')
    if not prompt:
        return jsonify({"error": "Prompt is required."}), 400
    try:
        response = openai.Completion.create(
            engine="text-davinci-003",
            prompt=prompt,
            max_tokens=150
        )
        return jsonify({"generated_text": response.choices[0].text.strip()})
    except Exception as e:
        return jsonify({"error": str(e)}), 500

# API Route: Generate Image (DALL·E API)
@app.route('/api/generate-image', methods=['POST'])
def generate_image():
    data = request.json
    prompt = data.get('prompt', '')
    if not prompt:
        return jsonify({"error": "Prompt is required."}), 400
    try:
        response = openai.Image.create(
            prompt=prompt,
            n=1,
            size="1024x1024"
        )
        return jsonify({"image_url": response['data'][0]['url']})
    except Exception as e:
        return jsonify({"error": str(e)}), 500

# API Route: Capstone Submission
@app.route('/api/submit-capstone', methods=['POST'])
def submit_capstone():
    data = request.json
    project_title = data.get('title', '')
    project_description = data.get('description', '')
    if not project_title or not project_description:
        return jsonify({"error": "Title and description are required."}), 400
    return jsonify({"message": "Capstone project submitted successfully!", "title": project_title})

# Run the Flask App
if __name__ == '__main__':
    app.run(debug=True)
