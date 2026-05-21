import pandas as pd
import matplotlib.pyplot as plt
file_path = "API_SP.POP.TOTL_DS2_en_csv_v2_38144.csv"
df = pd.read_csv(file_path, skiprows=4)
print(df.columns.tolist())
numeric_cols = df.select_dtypes(include=['number']).columns.tolist()
year_cols = [col for col in numeric_cols if str(col).isdigit()]
selected_col = year_cols[-1]
plt.figure(figsize=(10,6))
df[selected_col].dropna().plot(
    kind='hist',
    bins=20
)
plt.xlabel(f"Population in {selected_col}")
plt.ylabel("Frequency")
plt.title(f"Histogram of Population Distribution ({selected_col})")
plt.show()
