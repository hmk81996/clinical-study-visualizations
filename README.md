# Data-Visualization-Challenge

Xpert Learning Assistant resource use:

1) code framework for identifying duplicates = df[df.duplicated(subset=['column1', 'column2'])]

2) code for dropping duplicate: clean_df = df.drop_duplicates(subset=['Mouse ID'], keep='first')

3) code framework for groupby: grouped_df = clean_df.groupby("Drug Regimen")["Tumor Volume (mm3)"] and confirimed the summary statistics code I had written

4) corrected a code error: timepoints_sorted = timepoints.sort_values(ascending=False)

5) showed  how to efficiently combine two rows of code I had previously made: gender_group = clean_df.groupby('Sex')['Mouse ID'].count()

6) helped to debug and fix some errors with my labels and counts
genders = gender_group.index
gender_count = gender_group.values

7) helped to correct the merge on=['Mouse ID', 'Timepoint']
final_tumor_volume_df = pd.merge(last_timepoint, clean_df, on=['Mouse ID', 'Timepoint'])

8) recommended a dictionary instead of a list so treatments could be stored as keys
tumor_vol_data = {}

9) helped to identify necessary variables, provided the boolean operation == treatement, and the correct function to add to the dictionary

    match treatment in treatments list as a key 
    treatment_data = final_tumor_volume_df[final_tumor_volume_df['Drug Regimen'] == treatment]

    collect the volume as a value that corresponds to each treatement
    final_volumes = treatment_data['Tumor Volume (mm3)']

    add the resulting final tumor volumes for each drug to the empty list
    tumor_vol_data[treatment] = final_volumes.tolist()

    Xpert Learning Assistant provided this code
    final_volumes_series = pd.Series(final_volumes)

10) Xpert Assistant suggestion for correctly accessing dictionary keys and values
tumor_vol_df = pd.DataFrame(dict([(k, pd.Series(v)) for k, v in tumor_vol_data.items()]))

11)  code framework which I modified for this data 
mouse_b128 = clean_df[clean_df["Mouse ID"] ==  'b128']

12) reminded me to use the groupby function to get the avg tumor volume for each mouse
avg_tumor_volume = mouse_data.groupby("Mouse ID")["Tumor Volume (mm3)"].mean().reset_index()

13) recommended merging the tumor volume data back with my filtered-by-drug-regimen data
merged_mouse_data = mouse_data.groupby("Mouse ID")['Weight (g)'].first().reset_index()
