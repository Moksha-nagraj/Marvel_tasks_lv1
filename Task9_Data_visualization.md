import plotly.express as px<br>
import plotly.graph_objects as go<br>
import seaborn as sns<br>
import pandas as pd<br>

# Load the Iris dataset
iris = sns.load_dataset('iris')

# Example 1: Pair plot
fig_pair = px.scatter_matrix(iris, dimensions=['sepal_length', 'sepal_width', 'petal_length', 'petal_width'], color='species')<br>
fig_pair.update_layout(title='Pair Plot')<br>
fig_pair.show()<br>
![Alt PairPlot](https://github.com/Moksha-nagraj/Marvel_tasks_lv1/blob/main/newplot%20(3).png)

# Example 2: Heatmap
fig_heatmap = px.imshow(iris.corr(numeric_only=True), color_continuous_scale='Viridis')<br>
fig_heatmap.update_layout(title='Heatmap of Correlation Matrix', xaxis_title='Features', yaxis_title='Features')<br>
fig_heatmap.show()<br>
![Alt HeatMap](https://github.com/Moksha-nagraj/Marvel_tasks_lv1/blob/main/newplot%20(4).png)

# Example 3: Box plot
fig_box = px.box(iris, x='species', y='petal_length', color='species')<br>
fig_box.update_layout(title='Box Plot of Petal Length by Species')<br>
fig_box.show()<br>
![Alt BoxPlot](https://github.com/Moksha-nagraj/Marvel_tasks_lv1/blob/main/newplot%20(5).png)

# Example 4: Histogram
fig_hist = px.histogram(iris, x='sepal_length', color='species', marginal='rug')<br>
fig_hist.update_layout(title='Histogram of Sepal Length')<br>
fig_hist.show()<br>
![Alt Histogram](https://github.com/Moksha-nagraj/Marvel_tasks_lv1/blob/main/newplot%20(6).png)

# Example 5: Sunburst plot
sunburst_data = iris.groupby(['species', 'sepal_length'])['species'].count().reset_index(name='count')<br>
fig_sunburst = px.sunburst(sunburst_data, path=['species', 'sepal_length'], values='count')<br>
fig_sunburst.update_layout(title='Sunburst Plot of Species and Sepal Length')<br>
fig_sunburst.show()<br>
![Alt SunBurst](https://github.com/Moksha-nagraj/Marvel_tasks_lv1/blob/main/newplot%20(7).png)
