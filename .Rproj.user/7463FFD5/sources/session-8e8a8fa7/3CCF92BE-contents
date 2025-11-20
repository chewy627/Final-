#this is how I create or set working directory within RStudio
setwd("/cloud/project")


sleep <- read_csv("Sleep_health_and_lifestyle_dataset.csv")

install.packages("pastecs")


library(pastecs)

by(sleep$`Sleep Duration`, sleep$Gender, stat.desc)

by(sleep$`Sleep Duration`, sleep$Occupation, stat.desc)


sleep <- read.csv("Sleep_health_and_lifestyle_dataset.csv", header=TRUE)
names(sleep)   
"Sleep.Duration" 
"Occupation" 
"Gender" 

sleep$Gender <- as.factor(sleep$Gender)
sleep$Occupation <- as.factor(sleep$Occupation)


#install the ggplot2 package
install.packages("ggplot2")


#Load the package and all of its dependencies
library(ggplot2)

##############
## BOX PLOT ##
##############




boxplot_Gender <- ggplot(sleep, aes(Gender  , Sleep.Duration))
boxplot_Gender + geom_boxplot() 


boxplot_occupation <- ggplot(sleep, aes(Occupation  , Sleep.Duration))
boxplot_occupation + geom_boxplot() 

install.packages("shiny")
library(shiny)
library(ggplot2)


# Convert necessary columns to factors
sleep$Gender <- as.factor(sleep$Gender)
sleep$Occupation <- as.factor(sleep$Occupation)

# UI: Define the user interface
ui <- fluidPage(
  
  # App title
  titlePanel("Sleep Duration Analysis"),
  
  # Sidebar layout with input and output definitions
  sidebarLayout(
    
    # Sidebar panel for selecting variables
    sidebarPanel(
      selectInput("group_var", 
                  label = "Choose a grouping variable",
                  choices = c("Gender", "Occupation"),
                  selected = "Gender")
    ),
    
    # Main panel to display the boxplot
    mainPanel(
      plotOutput("sleep_plot")
    )
  )
)

# Server: Define server logic required to draw the plot
server <- function(input, output) {
  
  # Reactive expression to generate the boxplot based on selected input
  output$sleep_plot <- renderPlot({
    
    # Create the boxplot based on the selected group variable
    ggplot(sleep, aes_string(x = input$group_var, y = "Sleep.Duration")) +
      geom_boxplot() +
      labs(title = paste("Boxplot of Sleep Duration by", input$group_var),
           x = input$group_var,
           y = "Sleep Duration") +
      theme_minimal()
  })
}

# Run the application
shinyApp(ui = ui, server = server)