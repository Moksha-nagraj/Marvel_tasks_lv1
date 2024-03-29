import plotly.express as px
import plotly.graph_objects as go
import seaborn as sns
import pandas as pd

# Load the Iris dataset
iris = sns.load_dataset('iris')

# Example 1: Pair plot
fig_pair = px.scatter_matrix(iris, dimensions=['sepal_length', 'sepal_width', 'petal_length', 'petal_width'], color='species')
fig_pair.update_layout(title='Pair Plot')
fig_pair.show()
![Alt PairPlot]()
# Example 2: Heatmap
fig_heatmap = px.imshow(iris.corr(numeric_only=True), color_continuous_scale='Viridis')
fig_heatmap.update_layout(title='Heatmap of Correlation Matrix', xaxis_title='Features', yaxis_title='Features')
fig_heatmap.show()

# Example 3: Box plot
fig_box = px.box(iris, x='species', y='petal_length', color='species')
fig_box.update_layout(title='Box Plot of Petal Length by Species')
fig_box.show()

# Example 4: Histogram
fig_hist = px.histogram(iris, x='sepal_length', color='species', marginal='rug')
fig_hist.update_layout(title='Histogram of Sepal Length')
fig_hist.show()

# Example 5: Sunburst plot
sunburst_data = iris.groupby(['species', 'sepal_length'])['species'].count().reset_index(name='count')
fig_sunburst = px.sunburst(sunburst_data, path=['species', 'sepal_length'], values='count')
fig_sunburst.update_layout(title='Sunburst Plot of Species and Sepal Length')
fig_sunburst.show()
