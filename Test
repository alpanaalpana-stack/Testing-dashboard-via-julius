import streamlit as st
import pandas as pd
import plotly.graph_objects as go

# Sample sales data
data = {
    "Month": ["Jan", "Feb", "Mar", "Apr", "May"],
    "Revenue": [12000, 15000, 17000, 16000, 20000],
    "Cost": [8000, 9000, 11000, 10000, 13000]
}

df = pd.DataFrame(data)
df["Profit"] = df["Revenue"] - df["Cost"]
df["Growth %"] = df["Revenue"].pct_change().fillna(0) * 100

# Streamlit App
st.set_page_config(page_title="Sales Dashboard", layout="wide")

st.title("📊 Sales Dashboard with Profit & Growth")

# Revenue, Cost, Profit Bar Chart
fig = go.Figure()
fig.add_bar(x=df["Month"], y=df["Revenue"], name="Revenue")
fig.add_bar(x=df["Month"], y=df["Cost"], name="Cost")
fig.add_trace(go.Scatter(x=df["Month"], y=df["Profit"], 
                         mode="lines+markers", name="Profit", line=dict(color="green")))

# Growth Trend (Secondary Y-Axis)
fig.add_trace(go.Scatter(x=df["Month"], y=df["Growth %"], 
                         mode="lines+markers", name="Growth %", yaxis="y2", line=dict(color="orange")))

fig.update_layout(
    title="Revenue, Cost, Profit & Growth Trend",
    xaxis=dict(title="Month"),
    yaxis=dict(title="Amount ($)"),
    yaxis2=dict(title="Growth %", overlaying="y", side="right")
)

st.plotly_chart(fig, use_container_width=True)

# Show Data Table
st.subheader("📋 Raw Data")
st.dataframe(df)
