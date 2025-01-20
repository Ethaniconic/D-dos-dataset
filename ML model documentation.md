# ML Model building for sentiment prediction

*Importing pandas for performing manipulation tasks on data**

  import pandas as pd

  data = pd.read_csv("updated-d-dos.csv")

*Import important tools from sklearn library for machine learning, model training.**

  from sklearn.preprocessing import StandardScaler
  from sklearn.preprocessing import MinMaxScaler
  from sklearn.cluster import KMeans
  import matplotlib.pyplot as plt

*Using MinMaxScaler to normalise the values and give them between the range of 0 and 1.**

  from sklearn.preprocessing import MinMaxScaler

  #Initialize the scaler
  scaler = MinMaxScaler()
  
  #Scale the Ratings column
  data['Scaled_Ratings'] = scaler.fit_transform(data[['Ratings']])
  
  #Display the updated dataset
  data.tail()
  
*Imports the KMeans class from sklearn.cluster, which is used to perform K-Means clustering.**

  from sklearn.cluster import KMeans

*Creates a range object containing integers from 1 to 10. Each integer represents a potential number of clusters for the K-Means algorithm.**

  K = range(1, 11)

*Initializes an empty list named distortions to store the inertia values calculated for each clustering attempt.**

  distortion = []

*Loop: Iterates over each value of k in the defined range.**

  for k in K:
    kmeans = KMeans(n_clusters=k, random_state=42)
    kmeans.fit(data[['Scaled_Ratings']])
    distortions.append(kmeans.inertia_)

*Initializes a KMeans object with n_clusters set to k. The random_state parameter ensures reproducibility by controlling the random number generator.**

  kmeans = KMeans(n_clusters=k, random_state=42)

*Fits the K-Means model to the Scaled_Ratings feature of the dataset. This feature should be preprocessed (e.g., scaled or normalized) to ensure effective clustering.**

  kmeans.fit(data[['Scaled_Ratings']])

*Appends the inertia value (the sum of squared distances of samples to their closest cluster center) to the distortions list. Lower inertia values indicate better clustering.**

  distortions.append(kmeans.inertia_)

*This visualization is typically used after performing K-Means clustering to help determine an appropriate number of clusters. By examining where the distortion values begin to level off (the "elbow"), practitioners can make an informed decision about selecting k for their clustering model.**

  plt.figure(figsize=(10, 6))
  
  plt.plot(range(1, 11), distortions, 'bx-')
  
  plt.xlabel('Number of clusters (k)')
  
  plt.ylabel('Distortion (Inertia)')

  plt.title('The Elbow Method showing the optimal k')

  plt.grid()

  plt.show()
