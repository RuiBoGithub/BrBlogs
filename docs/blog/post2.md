# plot_data.py
import pandas as pd
import matplotlib.pyplot as plt

def main():
    try:
        df = pd.read_csv('evaluation_data.csv')
        
        # Get parameters from user
        time_col = input("Enter timestamp column name: ").strip()
        y_cols = input("Enter 1-2 y-axis columns (comma-separated): ").split(',')
        y_cols = [col.strip() for col in y_cols]
        
        # Convert timestamp
        df[time_col] = pd.to_datetime(df[time_col])
        
        # Create plot
        plt.figure(figsize=(12, 6))
        ax = df.plot(x=time_col, y=y_cols[0])
        
        # Add second axis if needed
        if len(y_cols) == 2:
            ax2 = ax.twinx()
            df.plot(x=time_col, y=y_cols[1], ax=ax2, color='orange')
            ax2.set_ylabel(y_cols[1])
        
        ax.set_xlabel(time_col)
        ax.set_ylabel(y_cols[0])
        plt.title("Time Series Visualization")
        plt.tight_layout()
        plt.show()

    except Exception as e:
        print(f"Error: {str(e)}")

if __name__ == "__main__":
    main()