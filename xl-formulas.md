# xl-formulas

## Formulas

calculate days between two dates

    =DATEDIF(start, end, "D")   # "D" = days, "M" = months, "Y" = years
    =end - start                # also returns day count (end must be later)

extract parts of a date

    =TODAY()          # today's serial date (recalculates on open)
    =MONTH(date)      # 1–12
    =YEAR(date)       # four-digit year
    =DAY(date)        # 1–31
    =WEEKDAY(date, 2) # 1=Mon … 7=Sun  (mode 2 = ISO week, Mon start)


## Lookup & Logic

approximate-match grade lookup (table must be sorted ascending)

    =VLOOKUP(score, $E$2:$F$6, 2, TRUE)
    # TRUE  = approximate match: finds largest threshold ≤ score
    # FALSE = exact match

find position then return value from another column

    =INDEX(A2:A4, MATCH(MIN(E2:E4), E2:E4, 0))
    # MATCH returns the row position; INDEX returns the value at that row
    # 0 = exact match in MATCH

conditional value

    =IF(condition, value_if_true, value_if_false)
    =IF(E2<=400, "Yes", "No")


## Financial

monthly loan payment

    =PMT(rate/12, nper, -pv)
    # rate   annual interest rate (divide by 12 for monthly)
    # nper   total number of monthly payments
    # -pv    loan amount as negative (money received today)

    =PMT(0.065/12, 48, -12000)   # → $284.58/month


## Bitwise & Number Conversion

IPv4 network math

    =BITAND(ip, mask)              # network number (keep shared bits)
    =BITAND(ip, BITXOR(mask, 255)) # host number (isolate device bits)
    =BITOR(ip,  BITXOR(mask, 255)) # broadcast address (set all host bits to 1)

decimal ↔ binary

    =DEC2BIN(n, 8)   # decimal → 8-character binary string  (0–255 only)
    =BIN2DEC(b)      # binary string → decimal
