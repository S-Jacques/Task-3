# Task-3
Module Help
I cannot get the preprocess_covid_data_frame to run. Here are the details.

# Print the summary of the data frame
summary(data_frame)

# call `preprocess_covid_data_frame` function and assign it to a new data frame
preprocess_covid_data_frame <- preprocess_covid_data_frame(data_frame) {
    
    shape <- dim(data_frame)

    # Remove the World row
    data_frame<-data_frame[!(data_frame$`Country.or.region`=="World"),]
    # Remove the last row
    data_frame <- data_frame[1:172, ]
    
    # We dont need the Units and Ref columns, so can be removed
    data_frame["Ref."] <- NULL
    data_frame["Units.b."] <- NULL
    
    # Renaming the columns
    names(data_frame) <- c("country", "date", "tested", "confirmed", "confirmed.tested.ratio", "tested.population.ratio", "confirmed.population.ratio")
    
    # Convert column data types
    data_frame$country <- as.factor(data_frame$country)
    data_frame$date <- as.factor(data_frame$date)
    data_frame$tested <- as.numeric(gsub(",","",data_frame$tested))
    data_frame$confirmed <- as.numeric(gsub(",","",data_frame$confirmed))
    data_frame$'confirmed.tested.ratio' <- as.numeric(gsub(",","",data_frame$`confirmed.tested.ratio`))
    data_frame$'tested.population.ratio' <- as.numeric(gsub(",","",data_frame$`tested.population.ratio`))
    data_frame$'confirmed.population.ratio' <- as.numeric(gsub(",","",data_frame$`confirmed.population.ratio`))
    
    return(data_frame)
}
df <- preprocess_covid_data_frame(data_frame)
df
R Response:
Error in parse(text = x, srcfile = src): <text>:2:72: unexpected '{'
1: # call `preprocess_covid_data_frame` function and assign it to a new data frame
2: preprocess_covid_data_frame <- preprocess_covid_data_frame(data_frame) {
                                                                          ^
Traceback:
