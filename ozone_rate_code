#ozone rate app
#data.3i

library(shiny)
data(airquality)

#define ui
ui <- fluidPage(
  
  titlePanel("Ozone rate"),
  
  sidebarLayout(
    
    #panel for inputs
    sidebarPanel(
      
      # n intervals
      sliderInput(inputId = "bins",
                  label = "Interval gap:",
                  min = 30,
                  max = 300,
                  value = 99)
      
    ),
    # panel for outputs
    
    mainPanel(
      
      # histogram
      plotOutput(outputId = "distPlot")
      
    )
  )
)

# set server logic fr hist
#' Title
#'
#' @param input 
#' @param output 
#'
#' @return
#' @export
#'
#' @examples
server <- function(input, output) {
  

  output$distPlot <- renderPlot({
    
    x    <- airquality$Ozone
    x    <- na.omit(x)
    bins <- seq(min(x), max(x), length.out = input$bins + 1)
    
    hist(x, breaks = bins, col = "#1681BF", border = "#EE0E0E",
         xlab = "Ozone range",
         main = "Histogram of Ozone level", 
         sub = substitute(
                paste(
   italic( "*Ozone range based on the series of intervals.Data is not cited."))
                ))
  })
  
}
# create app
shinyApp(ui = ui, server = server)
