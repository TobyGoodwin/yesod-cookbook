# Formatting date strings

Add old-locale to .cabal.

    import Data.Time
    import System.Locale (defaultTimeLocale)
    
    dateFormat = "%e %b %Y"
    dateFormat :: String
    dateTimeFormat = "%e %b %Y %H:%M:%S"
    dateTimeFormat :: String
    
    formatDate :: String -> String
    formatDate dateString = formatTime defaultTimeLocale dateTimeFormat t
        where 
            t = read dateString
            t :: UTCTime
        
    main = print $ formatDate "2012-09-15 00:07:31.874712 UTC"

# Formatting day values
Useful when you use a Day field and jQuery date picker.


    import Data.Time
    import System.Locale (defaultTimeLocale)
    
    dateFormat = "%e %b %Y"
    dateFormat :: String
    dateTimeFormat = "%e %b %Y %H:%M:%S"
    dateTimeFormat :: String
    
    formatDay :: Day -> String
    formatDay day = formatTime defaultTimeLocale dateFormat t
        where 
            t = UTCTime day 0
            t :: UTCTime
        
    main = do
        now <- getCurrentTime
        let today = utctDay now
        print $ formatDay today