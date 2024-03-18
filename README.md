# Correlation-between-the-time-students-spend-on-social-media-and-their-well-being
#This is a personal project to analyze the correlation between the time students spend on social media and their well being

import pandas as pd
import numpy as np
from scipy.stats import pearsonr
import matplotlib.pyplot as plt

# Step 1: Mock Data Creation
def create_dataset(n=100):
    """
    Creates a mock dataset of student social media usage and their well-being.
    
    Args:
        n (int): Number of students (entries) in the dataset.
    
    Returns:
        DataFrame: A pandas DataFrame with student IDs, social media usage (hours/day), and well-being scores.
    """
    np.random.seed(42)  # Ensuring reproducibility
    student_ids = np.arange(1, n + 1)
    social_media_usage = np.random.uniform(0.5, 5, n)  # Assuming 0.5 to 5 hours of social media usage per day
    well_being_scores = np.random.uniform(3, 10, n)  # Well-being scores ranging from 3 to 10
    
    return pd.DataFrame({'StudentID': student_ids, 'SocialMediaUsage': social_media_usage, 'WellBeingScore': well_being_scores})

# Step 2: Correlation Analysis
def analyze_correlation(df):
    """
    Analyzes the correlation between social media usage and well-being scores.
    
    Args:
        df (DataFrame): The dataset with social media usage and well-being scores.
    
    Returns:
        float: The Pearson correlation coefficient between social media usage and well-being scores.
    """
    correlation, _ = pearsonr(df['SocialMediaUsage'], df['WellBeingScore'])
    return correlation

# Visualizing Data and Correlation
def visualize_data(df):
    """
    Generates a scatter plot to visualize the relationship between social media usage and well-being scores.
    
    Args:
        df (DataFrame): The dataset with social media usage and well-being scores.
    """
    plt.figure(figsize=(10, 6))
    plt.scatter(df['SocialMediaUsage'], df['WellBeingScore'], alpha=0.6)
    plt.title('Social Media Usage vs. Well-Being Score')
    plt.xlabel('Social Media Usage (hours/day)')
    plt.ylabel('Well-Being Score')
    plt.grid(True)
    plt.show()

# Main function to execute the workflow
def main():
    df = create_dataset()
    correlation = analyze_correlation(df)
    print(f"Correlation between social media usage and well-being score: {correlation:.3f}")
    
    # Visualizing the data and correlation
    visualize_data(df)

# main()
