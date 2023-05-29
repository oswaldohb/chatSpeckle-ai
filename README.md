# 🗣️🔷 chatSpeckle (ai-feature-prototype)

Experience the power of AI and Speckle using pandasai, OpenAI, specklepy and streamlit.
This feature was built on top of a previous web app created in a speckle video tutorial called "Create Schedule from Revit Data", which you can follow as well.

Otherwise, you can just download/clone this repository, run streamlit, add your own OpenAI key and write queries to chatSpeckle.

>What was built on top of "Create Schedule from Revit Data" web app?

- Library
```python
from pandasai import PandasAI
from pandasai.llm.openai import OpenAI
```

- Function

```python
def chat_speckle(df,prompt):
    llm = OpenAI(api_token = OPENAI_API_KEY)
    pandas_ai = PandasAI(llm, conversational=False)
    result = pandas_ai.run(df, prompt=prompt)
    print(result)
    return result
```

- chatSpeckle feature 
```python
    col1, col2 = st.columns([1,1])
    with col1:
        result = st.dataframe(result_DF)
    with col2:
        st.info("⬇️chatSpeckle⬇️")
        OPENAI_API_KEY = st.text_input('OpenAI key',"sk-...vDlY")
        input_text = st.text_area('Enter your query')
        if input_text is not None:
            if st.button ("Send"):
                st.info('Your query:'+input_text)
                result = chat_with_speckle(result_DF, input_text)
                st.success(result)
```