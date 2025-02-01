Here is the screenshot of python coding for UI creation: 
<img width="1470" alt="Screenshot 2025-02-02 at 01 44 07" src="https://github.com/user-attachments/assets/19281477-f52f-48b5-b425-157f4c553f69" />

Full app.py (Streamlit UI)
import streamlit as st
import pandas as pd
from ai_query_agent import generate_sql_query, ask_database
from predict_trend import predict_air_quality_trend

# 🌍 Title and description
st.title("🌍 AI-Powered Air Quality Query Agent")
st.write("Enter your question about air quality data, and AI will retrieve the relevant information.")

# 🔎 User input field for air quality queries
user_query = st.text_input("🔎 Ask a question:", placeholder="What is the air quality in New York City?")

# 🏁 Query execution button
if st.button("Run Query"):
    if user_query:
        sql_query = generate_sql_query(user_query)
        results = ask_database(sql_query)

        # ✅ Show query results if found
        if isinstance(results, list) and results:
            df = pd.DataFrame(results, columns=["Location", "PM2.5", "Year"])
            st.success("✅ Query executed successfully!")
            st.table(df)  # Display results in a table
        
        # ⚠️ No data found, redirect user to OpenWeather
        else:
            st.warning("⚠️ No data found for this query. Please visit [OpenWeather](https://openweathermap.org/) for real-time air quality information.")

    else:
        st.error("⚠️ Please enter a valid question.")

# 📈 Future Air Quality Prediction Section
st.header("📈 Predict Future Air Quality Trends")

# 🌍 User input for city prediction
location_input = st.text_input("🌍 Enter a location:", placeholder="e.g., London")

# 🚀 Prediction button
if st.button("Predict Trend"):
    if location_input:
        prediction = predict_air_quality_trend(location_input)
        st.write(prediction)
    else:
        st.error("⚠️ Please enter a location.")
