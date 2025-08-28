from rapidfuzz.distance import JaroWinkler

threshold=0.8 
   # Limpiar 'nombreendocumento_limpio' en df_merged
df_merged['nombreendocumento_limpio'] = df_merged['nombreendocumento'].astype(str).apply(
        lambda x: unidecode(x).upper().strip()
    )

    # Calcular la similitud usando Jaro-Winkler
df_merged['similarity_score'] = df_merged.apply(
        lambda row: JaroWinkler.similarity(row['nombreendocumento_limpio'], row['full_name_limpio']) if pd.notnull(row['full_name_limpio']) else 0,
        axis=1
    )

    # Filtrar los que cumplen con el umbral
df_matched = df_merged[df_merged['similarity_score'] > threshold]
