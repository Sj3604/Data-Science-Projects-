---
jupyter:
  colab:
    authorship_tag: ABX9TyMImJGvCDaSZcllPQBIU5hV
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

::: {.cell .code execution_count="1" colab="{\"base_uri\":\"https://localhost:8080/\"}" executionInfo="{\"elapsed\":552,\"status\":\"ok\",\"timestamp\":1756634646781,\"user\":{\"displayName\":\"Shagun Jain\",\"userId\":\"04974469163623588661\"},\"user_tz\":-330}" id="e0NmAaRIk_wl" outputId="57f0b9ae-606b-49c4-b4cf-7ac5189c8de0"}
``` python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("/content/GOI.csv")
print(df.head())
print(df.info())
```

::: {.output .stream .stdout}
      Category Country/ States/ Union Territories Name  \
    0  Country                                   INDIA   
    1    State                          Andhra Pradesh   
    2    State                       Arunachal Pradesh   
    3    State                                   Assam   
    4    State                                   Bihar   

       Literacy Rate (Persons) - Total - 2001  \
    0                                    64.8   
    1                                    60.5   
    2                                    54.3   
    3                                    63.3   
    4                                    47.0   

       Literacy Rate (Persons) - Total - 2011  \
    0                                    73.0   
    1                                    67.0   
    2                                    65.4   
    3                                    72.2   
    4                                    61.8   

       Literacy Rate (Persons) - Rural - 2001  \
    0                                    58.7   
    1                                    54.5   
    2                                    47.8   
    3                                    59.7   
    4                                    43.9   

       Literacy Rate (Persons) - Rural - 2011  \
    0                                    67.8   
    1                                    60.4   
    2                                    59.9   
    3                                    69.3   
    4                                    59.8   

       Literacy Rate (Persons) - Urban - 2001  \
    0                                    79.9   
    1                                    76.1   
    2                                    78.3   
    3                                    85.3   
    4                                    71.9   

       Literacy Rate (Persons) - Urban - 2011  
    0                                    84.1  
    1                                    80.1  
    2                                    82.9  
    3                                    88.5  
    4                                    76.9  
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 36 entries, 0 to 35
    Data columns (total 8 columns):
     #   Column                                   Non-Null Count  Dtype  
    ---  ------                                   --------------  -----  
     0   Category                                 36 non-null     object 
     1   Country/ States/ Union Territories Name  36 non-null     object 
     2   Literacy Rate (Persons) - Total - 2001   36 non-null     float64
     3   Literacy Rate (Persons) - Total - 2011   36 non-null     float64
     4   Literacy Rate (Persons) - Rural - 2001   36 non-null     float64
     5   Literacy Rate (Persons) - Rural - 2011   36 non-null     float64
     6   Literacy Rate (Persons) - Urban - 2001   36 non-null     float64
     7   Literacy Rate (Persons) - Urban - 2011   36 non-null     float64
    dtypes: float64(6), object(2)
    memory usage: 2.4+ KB
    None
:::
:::

::: {.cell .markdown id="5d81ad7d"}
# Task

Analyze the urban literacy level of all Indian states using the data in
\"india_literacy_rate.csv\".
:::

::: {.cell .markdown id="cb35a9bf"}
**Reasoning**: Filter the DataFrame to include only states and select
the specified urban literacy rate columns.
:::

::: {.cell .code execution_count="2" colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":223}" executionInfo="{\"elapsed\":36,\"status\":\"ok\",\"timestamp\":1756634799235,\"user\":{\"displayName\":\"Shagun Jain\",\"userId\":\"04974469163623588661\"},\"user_tz\":-330}" id="c19cd8dd" outputId="a050c7e6-dd68-4d16-9c00-c5a3b3e7b84f"}
``` python
df_states_urban = df[df['Category'] == 'State']
df_states_urban = df_states_urban[['Country/ States/ Union Territories Name', 'Literacy Rate (Persons) - Urban - 2001', 'Literacy Rate (Persons) - Urban - 2011']]
display(df_states_urban.head())
```

::: {.output .display_data}
``` json
{"summary":"{\n  \"name\": \"display(df_states_urban\",\n  \"rows\": 5,\n  \"fields\": [\n    {\n      \"column\": \"Country/ States/ Union Territories Name\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 5,\n        \"samples\": [\n          \"Arunachal Pradesh\",\n          \"Chhattisgarh\",\n          \"Assam\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Literacy Rate (Persons) - Urban - 2001\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 4.999799995999838,\n        \"min\": 71.9,\n        \"max\": 85.3,\n        \"num_unique_values\": 5,\n        \"samples\": [\n          78.3,\n          80.6,\n          85.3\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Literacy Rate (Persons) - Urban - 2011\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 4.345342334039977,\n        \"min\": 76.9,\n        \"max\": 88.5,\n        \"num_unique_values\": 5,\n        \"samples\": [\n          82.9,\n          84.0,\n          88.5\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}","type":"dataframe"}
```
:::
:::

::: {.cell .markdown id="756a754a"}
**Reasoning**: Create a bar plot to compare the urban literacy rates for
each state in 2001 and 2011 following the instructions.
:::

::: {.cell .code execution_count="3" colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":471}" executionInfo="{\"elapsed\":2246,\"status\":\"ok\",\"timestamp\":1756634819997,\"user\":{\"displayName\":\"Shagun Jain\",\"userId\":\"04974469163623588661\"},\"user_tz\":-330}" id="40597c2e" outputId="1be65d2d-d3fa-4ad6-bc99-eec53fb74c87"}
``` python
fig, ax = plt.subplots(figsize=(15, 8))
bar_width = 0.35
index = np.arange(len(df_states_urban))
bar1 = ax.bar(index, df_states_urban['Literacy Rate (Persons) - Urban - 2001'], bar_width, label='2001')
bar2 = ax.bar(index + bar_width, df_states_urban['Literacy Rate (Persons) - Urban - 2011'], bar_width, label='2011')
ax.set_xticks(index + bar_width / 2)
ax.set_xticklabels(df_states_urban['Country/ States/ Union Territories Name'], rotation=90)
ax.legend()
ax.set_title("Urban Literacy Rate Comparison (2001 vs 2011)")
ax.set_ylabel("Literacy Rate (%)")
fig.tight_layout()
plt.show()
```

::: {.output .display_data}
![](6c740fb2bf7ef24f9938fbd49195e61a2c8093e2.png)
:::
:::

::: {.cell .markdown id="cfd4adf6"}
**Reasoning**: Analyze the generated bar plot to summarize the findings
about urban literacy rates across states, highlighting significant
changes and differences between 2001 and 2011.
:::

::: {.cell .markdown id="a58aa00b"}
## Summary:

### Data Analysis Key Findings

-   The urban literacy rates generally increased across most Indian
    states between 2001 and 2011.
-   Kerala demonstrated consistently high urban literacy rates in both
    2001 and 2011.
-   Bihar had among the lowest urban literacy rates in both years but
    showed an improvement over the decade.

### Insights or Next Steps

-   Investigate the factors contributing to the significant increase in
    urban literacy rates in states that showed the most improvement.
-   Analyze the disparity between urban and rural literacy rates for
    each state to understand the full literacy landscape.
:::

::: {.cell .markdown id="e73be736"}
**Reasoning**: Filter the DataFrame to include only states and select
the specified rural literacy rate columns, then create a bar plot to
compare the rural literacy rates for each state in 2001 and 2011.
:::

::: {.cell .code execution_count="5" colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":471}" executionInfo="{\"elapsed\":177,\"status\":\"ok\",\"timestamp\":1756635043593,\"user\":{\"displayName\":\"Shagun Jain\",\"userId\":\"04974469163623588661\"},\"user_tz\":-330}" id="ba09fe4b" outputId="0ad02441-e3aa-437f-fade-b889c6b42ef3"}
``` python
df_states_rural = df[df['Category'] == 'State']
df_states_rural = df_states_rural[['Country/ States/ Union Territories Name', 'Literacy Rate (Persons) - Rural - 2001', 'Literacy Rate (Persons) - Rural - 2011']]

fig, ax = plt.subplots(figsize=(15, 8))
bar_width = 0.35
index = np.arange(len(df_states_rural))
bar1 = ax.bar(index, df_states_rural['Literacy Rate (Persons) - Rural - 2001'], bar_width, label='2001')
bar2 = ax.bar(index + bar_width, df_states_rural['Literacy Rate (Persons) - Rural - 2011'], bar_width, label='2011')
ax.set_xticks(index + bar_width / 2)
ax.set_xticklabels(df_states_rural['Country/ States/ Union Territories Name'], rotation=90)
ax.legend()
ax.set_title("Rural Literacy Rate Comparison (2001 vs 2011)")
ax.set_ylabel("Literacy Rate (%)")
fig.tight_layout()
plt.show()
```

::: {.output .display_data}
![](8baa3ab4a37d6fccb6995791973e1e518ee21900.png)
:::
:::

::: {.cell .markdown id="48323ede"}
**Reasoning**: Analyze the generated bar plot to summarize the findings
about rural literacy rates across states, highlighting significant
changes and differences between 2001 and 2011.
:::

::: {.cell .markdown id="d77eaef3"}
## Summary: {#summary}

### Data Analysis Key Findings {#data-analysis-key-findings}

-   Similar to urban areas, rural literacy rates also showed a general
    increase across most Indian states between 2001 and 2011.
-   Kerala consistently had high rural literacy rates in both 2001 and
    2011, aligning with its urban literacy trend.
-   States like Bihar, Jharkhand, and Uttar Pradesh, which had lower
    urban literacy rates, also exhibited lower rural literacy rates,
    although improvements were observed.
-   The gap between rural and urban literacy rates appears to vary
    across states.

### Insights or Next Steps {#insights-or-next-steps}

-   Further investigate the specific programs and initiatives
    implemented in states with significant rural literacy rate
    improvements to identify best practices.
-   Quantify the urban-rural literacy gap for each state to understand
    the extent of the disparity and inform targeted interventions.
-   Analyze other factors that might influence rural literacy, such as
    access to education, socioeconomic conditions, and cultural factors.
:::

::: {.cell .markdown id="80ce8eb5"}
# Task {#task}

Analyze and compare the urban and rural literacy rates of Bihar and
Kerala for the years 2001 and 2011 using the file
\"india_literacy_rate.csv\".
:::

::: {.cell .markdown id="8665ddcf"}
**Reasoning**: Filter the original DataFrame to include only the rows
corresponding to Bihar and Kerala states.
:::

::: {.cell .code execution_count="6" colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":181}" executionInfo="{\"elapsed\":1347,\"status\":\"ok\",\"timestamp\":1756635233117,\"user\":{\"displayName\":\"Shagun Jain\",\"userId\":\"04974469163623588661\"},\"user_tz\":-330}" id="9719e194" outputId="0305d8c7-a907-4074-898c-7575c366353c"}
``` python
df_bihar_kerala = df[df['Country/ States/ Union Territories Name'].isin(['Bihar', 'Kerala'])]
display(df_bihar_kerala.head())
```

::: {.output .display_data}
``` json
{"summary":"{\n  \"name\": \"display(df_bihar_kerala\",\n  \"rows\": 2,\n  \"fields\": [\n    {\n      \"column\": \"Category\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 1,\n        \"samples\": [\n          \"State\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Country/ States/ Union Territories Name\",\n      \"properties\": {\n        \"dtype\": \"string\",\n        \"num_unique_values\": 2,\n        \"samples\": [\n          \"Kerala\"\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Literacy Rate (Persons) - Total - 2001\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 31.04198769408944,\n        \"min\": 47.0,\n        \"max\": 90.9,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          90.9\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Literacy Rate (Persons) - Total - 2011\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 22.76883835420683,\n        \"min\": 61.8,\n        \"max\": 94.0,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          94.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Literacy Rate (Persons) - Rural - 2001\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 32.597622612699844,\n        \"min\": 43.9,\n        \"max\": 90.0,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          90.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Literacy Rate (Persons) - Rural - 2011\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 23.47594513539338,\n        \"min\": 59.8,\n        \"max\": 93.0,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          93.0\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Literacy Rate (Persons) - Urban - 2001\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 15.061374439273461,\n        \"min\": 71.9,\n        \"max\": 93.2,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          93.2\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"Literacy Rate (Persons) - Urban - 2011\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 12.869343417595157,\n        \"min\": 76.9,\n        \"max\": 95.1,\n        \"num_unique_values\": 2,\n        \"samples\": [\n          95.1\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}","type":"dataframe"}
```
:::
:::

::: {.cell .markdown id="a196874a"}
**Reasoning**: Melt the filtered DataFrame to reshape it for easier
plotting and then extract the year and area type into new columns.
:::

::: {.cell .code execution_count="10" executionInfo="{\"elapsed\":6,\"status\":\"ok\",\"timestamp\":1756635369340,\"user\":{\"displayName\":\"Shagun Jain\",\"userId\":\"04974469163623588661\"},\"user_tz\":-330}" id="edbcb85b"}
``` python
df_melted = pd.melt(df_bihar_kerala, id_vars=['Category', 'Country/ States/ Union Territories Name'],
                    value_vars=['Literacy Rate (Persons) - Urban - 2001',
                                'Literacy Rate (Persons) - Urban - 2011',
                                'Literacy Rate (Persons) - Rural - 2001',
                                'Literacy Rate (Persons) - Rural - 2011'],
                    var_name='Literacy Type', value_name='Literacy Rate')
df_melted['Year'] = df_melted['Literacy Type'].str.extract(r'(\d{4})')
df_melted['Area Type'] = df_melted['Literacy Type'].str.extract(r'(Urban|Rural)')
```
:::

::: {.cell .markdown id="132ec613"}
**Reasoning**: Pivot the melted DataFrame to prepare it for plotting and
reset the index.
:::

::: {.cell .code execution_count="11" executionInfo="{\"elapsed\":31,\"status\":\"ok\",\"timestamp\":1756635384697,\"user\":{\"displayName\":\"Shagun Jain\",\"userId\":\"04974469163623588661\"},\"user_tz\":-330}" id="03c003cb"}
``` python
df_pivot = df_melted.pivot_table(index=['Country/ States/ Union Territories Name', 'Year', 'Area Type'],
                                 values='Literacy Rate').reset_index()
```
:::

::: {.cell .markdown id="2ff9e96b"}
**Reasoning**: Create a grouped bar plot using the pivoted DataFrame to
compare urban and rural literacy rates for Bihar and Kerala in 2001 and
2011, with appropriate labels and title.
:::

::: {.cell .code execution_count="12" colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":564}" executionInfo="{\"elapsed\":1543,\"status\":\"ok\",\"timestamp\":1756635389438,\"user\":{\"displayName\":\"Shagun Jain\",\"userId\":\"04974469163623588661\"},\"user_tz\":-330}" id="56a34b91" outputId="ebea7f5b-42cd-4971-91fd-ed785336b2ed"}
``` python
import seaborn as sns
plt.figure(figsize=(10, 6))
sns.barplot(x='Country/ States/ Union Territories Name', y='Literacy Rate', hue='Area Type', data=df_pivot, palette='viridis')
plt.title("Urban vs Rural Literacy Rate Comparison: Bihar and Kerala (2001 & 2011)")
plt.xlabel("State")
plt.ylabel("Literacy Rate (%)")
plt.show()
```

::: {.output .display_data}
![](7ca55bd6cada8113f63f81afe65597ab58f8f0cf.png)
:::
:::

::: {.cell .markdown id="33e11362"}
## Summary: {#summary}

### Data Analysis Key Findings {#data-analysis-key-findings}

-   In both Bihar and Kerala, urban literacy rates were consistently
    higher than rural literacy rates in both 2001 and 2011.
-   Kerala had significantly higher literacy rates overall (both urban
    and rural) compared to Bihar in both 2001 and 2011.
-   Both states showed an increase in literacy rates from 2001 to 2011.
-   The disparity between urban and rural literacy rates appeared to be
    more significant in Bihar than in Kerala.

### Insights or Next Steps {#insights-or-next-steps}

-   Investigate the factors contributing to the large urban-rural
    literacy gap, particularly in Bihar, and explore successful
    strategies employed in Kerala that could be replicated.
-   Further analyze the data by gender within urban and rural areas for
    each state to understand if there are additional disparities.
:::
