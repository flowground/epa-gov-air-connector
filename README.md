# ![LOGO](logo.png) U.S. EPA Enforcement and Compliance History Online (ECHO) - Clean Air Act **flow**ground Connector

## Description

A generated **flow**ground connector for the U.S. EPA Enforcement and Compliance History Online (ECHO) - Clean Air Act API (version 0.0.0).

Generated from: https://api.apis.guru/v2/specs/epa.gov/air/0.0.0/swagger.json<br/>
Generated at: 2019-05-07T17:40:21+03:00

## API Description

Enforcement and Compliance History Online (ECHO) is a tool developed and maintained by EPA's Office of Enforcement and Compliance Assurance for public use. ECHO provides integrated compliance and enforcement information for about 800,000 regulated facilities nationwide.
<BR><BR>Air Rest Services provides multiple service endpoints, each with specific capabilities, to search and retrieve data on facilities regulated under the Clean Air Act (CAA). The returned results reflect data drawn from EPA's ICIS-Air database.
<BR><BR>
The get_facilities, get_map, get_qid, and get_download end points are meant to be used together, while the enhanced get_facility_info end point is self contained.
  The get_facility_info end point returns either an array of state, county or zip clusters with summary statistics per cluster or an array of facilities.
<BR><BR>
The recommended use scenario for get_facilities, get_qid, get_map, and get_downoad is:
<br>
<br><b>1)</b>  Use get_facilities to validate passed query parameters, obtain summary statistics and to obtain a query_id (QID).  QIDs are time sensitive and will be valid for approximately 30 minutes.
<br><b>2)</b>  Use get_qid, with the returned QID, to paginate through arrays of facility results.
<br><b>3)</b>  Use get_map, with the returned QID, to zoom in/out and pan on the clustered and individual facility coordinates that meet the QID query criteria.
<br><b>4)</b>  Use get_download, with the returned QID, to generate a Comma Separated Value (CSV) file of facility information that meets the QID query criteria.
<br>
<br>
Use the qcolumns parameter to customize your search results.  Use the Metdata service endpoint for a list of available output objects, their Column Ids, and their definitions to help you build your customized output. 
<br><br>
Additional ECHO Resources:   <a href="https://echo.epa.gov/tools/web-services">Web Services</a>, <a href="https://echo.epa.gov/resources/echo-data/about-the-data">About ECHO's Data</a>, <a href="https://echo.epa.gov/tools/data-downloads">Data Downloads</a>
<br>

## Authorization

This API does not require authorization.

## Actions

### Clean Air Act Download Data Service

> Based on the QID obtained from a get_facilities or get_facility_info query, return a comma sepated vaule (CSV) file of the facilities found.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- CSV = Facility results formatted as comma delimited file download (default).
- GEOJSOND = Facility results formatted as GeoJSON feature collection download.
* `qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.
* `p_pretty_print` - _optional_ - Optional flag to request GeoJSON formatted results to be pretty printed.  Only provide a numeric value when the output needs to be human readable as pretty printing has a performance cost.

### Clean Air Act Download Data Service

> Based on the QID obtained from a get_facilities or get_facility_info query, return a comma sepated vaule (CSV) file of the facilities found.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- CSV = Facility results formatted as comma delimited file download (default).
- GEOJSOND = Facility results formatted as GeoJSON feature collection download.
* `qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.
* `p_pretty_print` - _optional_ - Optional flag to request GeoJSON formatted results to be pretty printed.  Only provide a numeric value when the output needs to be human readable as pretty printing has a performance cost.

### Clean Air Act Facility Search

> Validates query search parameters and returns query identifier.  Use the responseset parameter to set the page size

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
    Possible values: JSONP, JSON, XML.
* `p_fn` - _optional_ - Facility Name Filter. Enter one or more case-insensitive facility names to filter results.  Provide multiple values as a comma-delimited list.  See p_fntype for additional modifiers.
* `p_sa` - _optional_ - Facility street address. Enter a complete or partial street address.
* `p_sa1` - _optional_ - Facility street address. Enter a complete or partial street address.   Note that p_sa1 is culmulative with p_sa.
* `p_ct` - _optional_ - Facility City Filter. Enter a single case-insensitive city name to filter results.
* `p_co` - _optional_ - Facility County Filter. Provide a single county name in combination with a state value provided via p_st.
* `p_fips` - _optional_ - FIPS Code Filter.  Enter a single 5-character Federal Information Processing Standards (FIPS) state + county value to restrict results.  E.g. to limit results to Kenosha County, Wisconsin, use 55059.
* `p_st` - _optional_ - Facility State and State-Equivalent Filter.  Provide one or more USPS postal abbreviations for states and state-equivalents to filter results.  Provide multiple values as a comma-delimited list.
* `p_zip` - _optional_ - 5-Digit ZIP Code Filter. Provide one or more 5-digit postal zip codes to filter results.  May contain multiple comma-separated values.
* `p_lcon` - _optional_ - Air Program Local Control Region Code Filter.  Enter one or more local control region codes to filter results.  Provide multiple codes as a comma-delimited list.  Codes where they exist are specific by state.
* `p_frs` - _optional_ - Facility Registry Service ID Filter. Enter a single 12-digit FRS identifier to filter results.
* `p_reg` - _optional_ - EPA Region Filter. Provide a single value of 01 thru 10 to restrict results to a single EPA region.
    Possible values: 01, 02, 03, 04, 05, 06, 07, 08, 09, 10.
* `p_sic` - _optional_ - Standard Industrial Classification (SIC) Code Filter.  Enter a single 4-digit SIC Code to filter results.  If more complex filtering is required, use p_sic2 and p_sic4.
* `p_ncs` - _optional_ - North American Industry Classification System Filter. Enter two to six digits to filter results to facilities having matching NAICS codes.  Digits less than six will match to all codes beginning with the provided values.
* `p_qnc` - _optional_ - Number of quarters in non-compliance limiter.  Enter an integer value between 1 and 4 to limit results.
* `p_pen` - _optional_ - Last Penality Date Qualifier Filter.  Enter one of the following:   
- NEVER = No Penalties
- ANY = Any Penalty
- LEXX = Less than or equal to XX months.  Provide a number in place of XX, e.g. "LE5" for a facility with a penalty within previous 5 months.
- GTXX = Greater than XX months.  Provide a number in place of XX, eg. GT12, for a facility with the last penalty greater than 12 months ago.
* `p_opst` - _optional_ - Operating status filter.  Enter one or more operating status codes to limit results.   Provide multiple codes as a comma-delimited list.
* `p_c1lat` - _optional_ - In decimal degrees.  Latitude of 1st corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_c1lon` - _optional_ - In decimal degrees.  Longitude of 1st corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_c2lat` - _optional_ - In decimal degrees.  Latitude of 2nd corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_c2lon` - _optional_ - In decimal degrees.  Longitude of 2nd corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_usmex` - _optional_ - US-Mexico Border Flag.  Enter Y/N to restrict searches to facilities located within 100KM of the border.
    Possible values: Y, N.
* `p_sic2` - _optional_ - Standard Industrial Classification (SIC) Code Filter Alternate 2. Enter a wild-card search against SIC codes.  A final wild-card is always present allowing "22" to match all SIC codes beginning with 22.  Use the "%" character within strings to match any SIC values with the pattern.  For example, "2%21" matches 2021, 2121, 2221, etc.
* `p_sic4` - _optional_ - Standard Industrial Classification (SIC) Code Filter Alternate 3.  Enter the first 2, 3 or 4 SIC code digits to filter results to facilities having those code prefixes.  As this alternative does not utilize an index, p_sic2 will generally be quicker.
* `p_fa` - _optional_ - Federal Agency. 1 character or 5-character values; may contain multiple comma-separated values. ALL will retrieve all facilities where the federal agency code is not null.  Use the Federal Agencies lookup service to obtain a list of values.
* `p_act` - _optional_ - Active Permits/Facilities Flag.  Provide Y or N to filter results to facilities with active permits.
    Possible values: Y, N, A.
* `p_maj` - _optional_ - Major Facility Flag.  Enter Y to restrict results to Major facilities only.
    Possible values: Y, N.
* `p_mact` - _optional_ - CAA Maximum Achievable Control Technology (MACT) Subpart codes (alpha ID between 1 and 7 characters) applicable to the facility.
* `p_prog` - _optional_ - Air Program Code Filter.  Enter one or more Air program codes to filter results.  Provide multiple values as a comma-delimited list.
* `p_fea` - _optional_ - Formal Enforcement Actions [within / not within] specified date range indicator. The date range is determined by parameters p_fead1 and p_fead2 or by parameter p_feay.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_feay` - _optional_ - Years (1 to 5) Range.  This value is used to create a date range for Formal Enforcement Actions (FEA). Used along with p_fea (which indicates whether to look within or outside of the date range) to find FEAs within (or not within) the number of years specified.
    Possible values: 1, 2, 3, 4, 5.
* `p_feaa` - _optional_ - Agency associated with Formal Enforcement Actions:
- E = EPA
- S = State
- A = All
    Possible values: A, E, S.
* `p_iea` - _optional_ - Informal Enforcement Actions [within / not within] specified date range.  The date range is determined by parameters p_iead1 and p_iead2 or by parameter p_ieay.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_ieay` - _optional_ - Years (1 to 5) Range.  This value is used to create a date range for Informal Enforcement Actions (IEA). Used along with p_iea (which indicates whether to look within or outside of the date range) to find IEAs within (or not within) the number of years specified.
    Possible values: 1, 2, 3, 4, 5.
* `p_ieaa` - _optional_ - Agency associated with Informal Enforcement Actions. If left blank, both agencies are included.
- E = EPA
- S = State
    Possible values: E, S.
* `p_qiv` - _optional_ - Quarters in Noncompliance Limiter.  Enter a coded value to limit results to facilities with given quarter of noncompliance.
- Z = Zero quarters in noncompliance.
- GEXX = Replacing XX with a numeric value, that number of quarterd or more in noncompliance.
- GTXX = Replacing XX with a numeric value, more than that number of quarters in noncompliance.
    Possible values: 0, GT1, GT2, GT4, GT8, 12.
* `p_naa` - _optional_ - Non-Attainment Area Flag.  Enter a Y or N to filter for or against facilities flagged as non-attainment areas.
* `p_impw` - _optional_ - Discharging into Impaired Waters Flag. Enter Y to limit results to facilities with discharge to waterbodies listed as impaired in the ATTAINS database.
    Possible values: Y, N.
* `p_trep` - _optional_ - Current Toxics Release Inventory (TRI) Reporter Limiter.  Enter one of the following codes to limit results.
- NONE = Never has reported to TRI.
- CURR = Current TRI reporter.
- NONCURR = Has reported to TRI in the past but not for the current reporting year.
    Possible values: NONE, CURR, NOTCURR.
* `p_tri_cat` - _optional_ - Toxic Release Inventory Released To Air Chemical Identifier Category Filter.  Enter the chemical identifier category code to limit results. Note when filtering by TRI chemical identifier categories one may not also filter by specific chemical identifiers via p_tri_pol.  You must also specify a release amount using p_tri_amt or p_tri_any_amt.
- TOTAL = Total Released to Air
- CARC = Total Carcinogens Released to Air
- HAP = Total Hazardous Air Pollutants Released to Air
    Possible values: TOTAL, CARC, HAP.
* `p_tri_amt` - _optional_ - Toxic Release Inventory Release Amount Filter.  Enter a value in pounds to limit results to facilities releasing this amount or greateer of TRI releases.  Valid values are 0, GT0, GT1000, GT5000, GT10000 and GT50000. Note when filtering by TRI release amounts one may only use either p_tri_amt or p_tri_any_amt.
    Possible values: 0, GT0, GT1000, GT5000, GT10000, GT50000.
* `p_tri_any_amt` - _optional_ - Toxic Release Inventory Release Of Any Kind Above Value Filter.  Enter a value to limit results to facilities releasing this amount or more of TRI releases.  Note when filtering by TRI releases one may only use p_tri_any_amt or p_tri_amt and not both.
* `p_tri_pol` - _optional_ - Toxic Release Inventory Chemical Identifier Filter.  Enter one or more chemical identifier codes to limit results. Note when filtering by specific TRI chemical identifiers one may not also filter by chemical identifier categories via p_tri_cat.
* `p_ghg_cat` - _optional_ - Green House Gas (GHG) Gas Code Category.  Must be used with either a formatted (p_ghg_amt) or custom (p_ghg_any_amt) release amount.
    Possible values: ALL, BIOCO2, CH4, CO2, HFC, N2O, NF3, OTHER_L, PFC, SF6.
* `p_ghg_amt` - _optional_ - Green House Gas (GHG) CO2 Equivalent Formatted Release Amount.  First 2 characters must contain GT (greater than) followed by a number.
    Possible values: None, 0, GT0, GT10000, GT25000, GT250000, GT1000000.
* `p_ghg_any_amt` - _optional_ - Green House Gas (GHG) C02 Equivalent Custom Amount.  The C02E value reported for the provided category, will be greater or equal to the amount provided.
* `p_ghg_yr` - _optional_ - Green House Gas (GHG) Reporting Year. (2010 through 2015)
* `p_nei_pol` - _optional_ - National Emissions Inventory (NEI) Pollutant Identifier.  When a pollutant identifer is entered a corresponding formatted amount or custom amount must be entered.
* `p_nei_amt` - _optional_ - National Emissions Inventory (NEI) Formatted Pollutant Amount.  A formatted value where the 1st two characters must start with GT or LT followed by a number.  Identifies facilities that have a NEI Pollutant Emission  where the supplied value is > or < the pollutant emission amount.  
    Possible values: None, 0, GT0, GT10000, GT25000, GT250000, GT1000000.
* `p_nei_any_amt` - _optional_ - National Emissions Inventory (NEI) Custom Pollutant Amount.  Only a number can be entered.  Identifies facilities with where the NEI Pollutant Emission Amount is greater than the number entered.
* `p_nei_yr` - _optional_ - National Emissions Inventory (NEI) year:  2014 or 2011
* `p_nei_cat` - _optional_ - National Emissions Inventory (NEI) Pollutant Category.  When a pollutant category is entered, a corresponding formatted pollutant amount or custom amount must be entered.
* `p_pm` - _optional_ - Percent Minority Population Limiter.  Enter a value to restrict results to facilities with a given percentage of minority population within 3-mile radius.
- NONE = 0%
- GT5 = greater than 5%
- GT10 = greater than 10%
- GT25 = greater than 25%
- GT50 = greater than 50%
- GT75 = greater than 75%
    Possible values: NONE, GT5, GT10, GT25, GT50, GT75.
* `p_pd` - _optional_ - Population Density Limiter (per sq mile). Enter a value to limit results to facilities located in area of a given population density.
- NONE = 0 population density per square mile
- GT100 = More than 100 population density per square mile
- GT500 = More than 500 population density per square mile
- GT1000 = More than 1000 population density per square mile
- GT5000 = More than 5000 population density per square mile
- GT10000 = More than 10000 population density per square mile
- GT20000 = More than 20000 population density per square mile
    Possible values: NONE, GT100, GT500, GT1000, GT5000, GT10000, GT20000.
* `p_ico` - _optional_ - Indian Country Flag.  Enter a "Y" or "N" to restrict searches to facilities inside or outside Indian Country.
    Possible values: Y, N.
* `p_huc` - _optional_ - 2-, 4-, 6-, or 8-character watershed. May contain multiple comma-separated values.
* `p_wbd` - _optional_ - 2-, 4-, 6-, 8-, 10-, or 12-character watershed (WBD from the USGS Watershed Boundary Dataset). May contain multiple comma-separated values.  Uses the FRS Best Pick Coordinate to obtain the WBD12 Huc value.
* `p_pid` - _optional_ - Nine-digit permit IDs. May contain up to 2000 comma-separated values.
* `p_med` - _optional_ - Filter Results by Media.
- M = RMP (Risk Management Plan)
- R = RCRA (Hazardous Waste)
- S = SDWA (Public Drinking Water Systems)
- W = Water
- ALL = Water and RCRA and SDWA
    Possible values: M, R, S, W, ALL.
* `p_ysl` - _optional_ - Last Facility Inspection [within / not within] Specified Date Range Indicator. The date range is determined by parameters p_idt1 and p_idt2 or by parameter p_ysly.
- W = within date range
- N = not within date range
    Possible values: W, N, NV.
* `p_ysly` - _optional_ - Number of years (1 to 5) since last facility inspection.  A value of 1 means that it has been inspected within the year.
    Possible values: 1, 2, 3, 4, 5.
* `p_ysla` - _optional_ - Facility Last Inspection Code Filter.  If left blank, both agencies are included.  Enter a value to limit results:
- E = EPA
- S = State
    Possible values: E, S, A.
* `p_stsl` - _optional_ - Last Stack Test [within / not within] Specified Date Range Indicator.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_stsly` - _optional_ - Number of years (1 to 5) since date of last stack test. A value of 1 means it has been inspected within the year.
    Possible values: 1, 2, 3, 4, 5.
* `p_stsla` - _optional_ - Stack Last Test Code Filter.  Enter a value to limit results:
- A = All
- E = EPA
- S = State
    Possible values: A, E, S.
* `p_stres` - _optional_ - Air Stack Test Status Description Filter.  Enter one or more test status descriptions to filter results.  Enter multiple values as a comma-delimited list.
* `p_sttyp` - _optional_ - Air Conductor Type Code Filter.  Enter one or more conductor type codes to filter results.  Provide multiple values as a comma-delimited list.
* `p_qs` - _optional_ - Quick Search. Allows entry for city, state, and/or zip code.
* `p_sfs` - _optional_ - Single Facility Search Filter.  Provide a facility name or program system identifier to limit results.  For the all data search, the FRS registry identifier is also searched.
* `p_tribeid` - _optional_ - Numeric code for tribe (or list of tribes).
* `p_tribename` - _optional_ - Tribe Name Filter.  Enter a single tribe name to filter results.
* `p_tribedist` - _optional_ - Proximity to tribal land limiter. Enter an amount of mile between 0 and 25 to filter results.  This parameter is only evaluated if p_tribeid is populated.
* `p_owop` - _optional_ - Owner/Operator code filter.  Enter one or more codes to limit results.
- CNG
- COR
- CTG
- DIS
- FDF
- MWD
- MXO
- NON
- POF
- SDT
- STF
- TRB
* `p_agoo` - _optional_ - Indicates whether to AND or OR the Owner/Operator parameter (p_owop) and the federal agency code (p_fa) parameters.
    Possible values: AND, OR.
* `p_idt1` - _optional_ - Beginning of date range of most recent facility inspection.
* `p_idt2` - _optional_ - End of date range of most recent facility inspection.
* `p_stdt1` - _optional_ - Beginning of date range of most recent stack test.
* `p_stdt2` - _optional_ - End of date range of most recent stack test.
* `p_pityp` - _optional_ - Inspection Type:
- CAC = Corrective Action Inspection
- CAV = Compliance Assistance Visit
- CDI = Case Development Inspection
- CEI = Inspection Inspection
- CSE = Compliance Schedule Evaluation
- FCI = Focused Compliance
- FRR = Financial Record Review
- FSD = Facility Self Disclosure
- FUI = Follow-Up Inspection
- GME = Groundwater Monitoring Evaluation
- NRR = Non-Financial Record Review
- OAM = Operation and Maintenance Inspection
May contain multiple comma-separated values.
* `p_cifdi` - _optional_ - Compliance issuess found during inspection.
    Possible values: Any, Yes, No, Undetermined.
* `p_pfead1` - _optional_ - Formal Enforcement Action Date Range Start.  Enter a date in MM/DD/YYYY format to set the start of the range for filtering by recent Formal Enforcement Action (FEA) taken against the facility within the last five years.
* `p_pfead2` - _optional_ - Formal Enforcement Action Date Range End.  Enter a date in MM/DD/YYYY format to set the end of the date range for filtering by recent Formal Enforcement Action (FEA) taken against the facility within the last five years.
* `p_pfeat` - _optional_ - Formal Enforcement Action (FEA) Code Filter.  Enter one or more three-letter FEA codes to restrict results to facilities with these attributes.  Use p_fead1 and p_fead2 parameters to further restrict this filter by entering a date range.  Provide multiple codes as a comma-delimited list.
* `p_psncq` - _optional_ - Quarters in Significant Noncompliance Limiter.  Enter a coded value to limit results to facilities with given quarter of significant noncompliance.
- Z = Zero quarters in significant noncompliance.
- GEXX = Replacing XX with a numeric value, that number of quarterd or more in significant noncompliance.
- GTXX = Replacing XX with a numeric value, more than that number of quarters in significant noncompliance.
    Possible values: GT1, GE1, GT2, GE2, GT4, GE4, GT8, GE8, GT12, GE12.
* `p_pctrack` - _optional_ - Compliance Tracking Limiter. Provide a keyword to indicate the extent to which data is being entered and effluent exceedances are being identified.
- Off
- Partial
- On
    Possible values: Off, Partial, On.
* `p_swpa` - _optional_ - Source water protection area
    Possible values: source water, surface water, ground water, waiting for SSO.
* `p_des` - _optional_ - Universe Designation Limiter.  Enter one or more universe designation codes.  Provide multiple values as a comma-delimited list.  Use code "TSDF" to return the full enforcement TSDF universe and "Operating TSDF" to return the operating TSDF universe.
* `p_fntype` - _optional_ - Controls type of text search performed on facility name with parameter p_fn.
- EXACT = Find facilities having the exact provided name(s).
- BEGINS = Find facilities with names starting with the provided term(s).
- ALL = Find facilities using Oracle text search terms.
- CONTAINS = 
    Possible values: ALL, CONTAINS, EXACT, BEGINS.
* `p_hpvmth` - _optional_ - Months in high priority violation status out of the previous three years limiter.  Provide a number of months in the past three years.  Results will limited to facilities in high priority violation status during that time. 
* `p_recvio` - _optional_ - Recent Violation Status Filter.  Enter one or more recent violation codes to limit results.  Provide multiple values as a comma-delimited list.
- NO VIOL = Selects facilities with no recent violations.
- ANY HPV = Selects facilities with either addressed or unaddressed high priority violations.
- ADDRS-EPA - Select facilities with recent EPA addressed violations.
- ADDRS-LOCAL - Select facilities with recent locally addressed violations.
- ADDRS-STATE - Select facilities with recent state addressed violations.
- UNADDR-EPA - Select facilities with recent EPA unaddressed violations.
- UNADDR-LOCAL - Select facilities with recent locally unaddressed violations.
- UNADDR-STATE - Select facilities with recent state unaddressed violations.
- FRV VIOL = Selects facilities with a recent federally reportable violation without a high priority violation.
* `p_pollvio` - _optional_ - Air Pollutant Code For A Recent Violation Filter.  Provide one or more pollutant codes to select facilities with one or more of the entered pollutant codes for a recent air violation.  Provide multiple values as a comma-delimited list.
* `p_ar` - _optional_ - Associated EPA Air Reports Program Filter.  Enter multiple values as a comma-delimited list.  Valid values are:
- TRI = Toxic Release Inventory.
- GHG = Green House Gas Reporter.
- EIS = Emission Inventory System.
- CAMD = Clean Air Markets Program Reporter.
* `p_tri_yr` - _optional_ - Toxic Release Inventory Reporting Year Filter.  Enter one or more year values to filter results by the TRI reporting year.  Provide multiple years as a comma-delimited list.
* `p_pidall` - _optional_ - Controls whether search is restricted to existing system. Y means the search will match the p_pid parameter against all associated permits (AIR, RCRA, SDWIS, etc).
    Possible values: Y, N.
* `p_fac_ico` - _optional_ - FRS tribal land code flag.  Enter "Y" or "N" to include or exclude facilities based on FRS tribal land code.
    Possible values: Y, N.
* `p_icoo` - _optional_ - Indian country search and/or flag.  Enter "Y" to set indian country search conditions to return any results found using p_ico, p_fac_ico or p_fac_icoo.  Otherwise only results matching all provided p_ico, p_fac_ico or p_fac_icoo conditions will be returned.
* `p_fac_icos` - _optional_ - FRS tribal land spatial flag.  Enter "Y" or "N" to include or exclude facilities based on FRS tribal land spatial flag.
* `p_ejscreen` - _optional_ - Enter "Y" to limit facilities to Census block groups where one of more Environmental Justice indexes above 80th percentile.
* `p_limit_addr` - _optional_ - Limit Address Search Flag.  Enter Y to restrict facility searches to native data source only.  
    Possible values: Y, N.
* `p_lat` - _optional_ - Latitude location in decimal degrees.
* `p_long` - _optional_ - Longitude location in decimal degrees.
* `p_radius` - _optional_ - Spatial Search Radius.  Enter a radius up to 100 miles in which to spatially search for facilities.
* `p_decouple` - _optional_ - Decouple Inspection Code Search Flag.  Enter "Y" to search for inspection code types with p_pityp without respect to the date range search provided with p_ysl* parameters.
    Possible values: Y, N.
* `p_ejscreen_over80cnt` - _optional_
* `queryset` - _optional_ - Query Limiter.  Enter a value to limit the number of records returned for each query. Value cannot exceed 70,000.
* `responseset` - _optional_ - Response Set Limiter. Enter a value to limit the number of records per page. Value cannot exceed 1,000.
* `tablelist` - _optional_ - Table List Flag. Enter a Y to display the first page of facility results.
    Possible values: Y, N.
* `maplist` - _optional_ - Map List Flag.  Provide a Y to return mappable coordinates representing the full geographic extent of the queryset (all facilities that met the selection criteria).
    Possible values: Y, N.
* `summarylist` - _optional_ - Summary List Flag.  Enter a Y to return a list of summary statistics based on the parameters submitted to the query service.
    Possible values: Y, N.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.

### Clean Air Act Facility Search

> Validates query search parameters and returns query identifier.  Use the responseset parameter to set the page size

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
    Possible values: JSONP, JSON, XML.
* `p_fn` - _optional_ - Facility Name Filter. Enter one or more case-insensitive facility names to filter results.  Provide multiple values as a comma-delimited list.  See p_fntype for additional modifiers.
* `p_sa` - _optional_ - Facility street address. Enter a complete or partial street address.
* `p_sa1` - _optional_ - Facility street address. Enter a complete or partial street address.   Note that p_sa1 is culmulative with p_sa.
* `p_ct` - _optional_ - Facility City Filter. Enter a single case-insensitive city name to filter results.
* `p_co` - _optional_ - Facility County Filter. Provide a single county name in combination with a state value provided via p_st.
* `p_fips` - _optional_ - FIPS Code Filter.  Enter a single 5-character Federal Information Processing Standards (FIPS) state + county value to restrict results.  E.g. to limit results to Kenosha County, Wisconsin, use 55059.
* `p_st` - _optional_ - Facility State and State-Equivalent Filter.  Provide one or more USPS postal abbreviations for states and state-equivalents to filter results.  Provide multiple values as a comma-delimited list.
* `p_zip` - _optional_ - 5-Digit ZIP Code Filter. Provide one or more 5-digit postal zip codes to filter results.  May contain multiple comma-separated values.
* `p_lcon` - _optional_ - Air Program Local Control Region Code Filter.  Enter one or more local control region codes to filter results.  Provide multiple codes as a comma-delimited list.  Codes where they exist are specific by state.
* `p_frs` - _optional_ - Facility Registry Service ID Filter. Enter a single 12-digit FRS identifier to filter results.
* `p_reg` - _optional_ - EPA Region Filter. Provide a single value of 01 thru 10 to restrict results to a single EPA region.
    Possible values: 01, 02, 03, 04, 05, 06, 07, 08, 09, 10.
* `p_sic` - _optional_ - Standard Industrial Classification (SIC) Code Filter.  Enter a single 4-digit SIC Code to filter results.  If more complex filtering is required, use p_sic2 and p_sic4.
* `p_ncs` - _optional_ - North American Industry Classification System Filter. Enter two to six digits to filter results to facilities having matching NAICS codes.  Digits less than six will match to all codes beginning with the provided values.
* `p_qnc` - _optional_ - Number of quarters in non-compliance limiter.  Enter an integer value between 1 and 4 to limit results.
* `p_pen` - _optional_ - Last Penality Date Qualifier Filter.  Enter one of the following:   
- NEVER = No Penalties
- ANY = Any Penalty
- LEXX = Less than or equal to XX months.  Provide a number in place of XX, e.g. "LE5" for a facility with a penalty within previous 5 months.
- GTXX = Greater than XX months.  Provide a number in place of XX, eg. GT12, for a facility with the last penalty greater than 12 months ago.
* `p_opst` - _optional_ - Operating status filter.  Enter one or more operating status codes to limit results.   Provide multiple codes as a comma-delimited list.
* `p_c1lat` - _optional_ - In decimal degrees.  Latitude of 1st corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_c1lon` - _optional_ - In decimal degrees.  Longitude of 1st corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_c2lat` - _optional_ - In decimal degrees.  Latitude of 2nd corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_c2lon` - _optional_ - In decimal degrees.  Longitude of 2nd corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_usmex` - _optional_ - US-Mexico Border Flag.  Enter Y/N to restrict searches to facilities located within 100KM of the border.
    Possible values: Y, N.
* `p_sic2` - _optional_ - Standard Industrial Classification (SIC) Code Filter Alternate 2. Enter a wild-card search against SIC codes.  A final wild-card is always present allowing "22" to match all SIC codes beginning with 22.  Use the "%" character within strings to match any SIC values with the pattern.  For example, "2%21" matches 2021, 2121, 2221, etc.
* `p_sic4` - _optional_ - Standard Industrial Classification (SIC) Code Filter Alternate 3.  Enter the first 2, 3 or 4 SIC code digits to filter results to facilities having those code prefixes.  As this alternative does not utilize an index, p_sic2 will generally be quicker.
* `p_fa` - _optional_ - Federal Agency. 1 character or 5-character values; may contain multiple comma-separated values. ALL will retrieve all facilities where the federal agency code is not null.  Use the Federal Agencies lookup service to obtain a list of values.
* `p_act` - _optional_ - Active Permits/Facilities Flag.  Provide Y or N to filter results to facilities with active permits.
    Possible values: Y, N, A.
* `p_maj` - _optional_ - Major Facility Flag.  Enter Y to restrict results to Major facilities only.
    Possible values: Y, N.
* `p_mact` - _optional_ - CAA Maximum Achievable Control Technology (MACT) Subpart codes (alpha ID between 1 and 7 characters) applicable to the facility.
* `p_prog` - _optional_ - Air Program Code Filter.  Enter one or more Air program codes to filter results.  Provide multiple values as a comma-delimited list.
* `p_fea` - _optional_ - Formal Enforcement Actions [within / not within] specified date range indicator. The date range is determined by parameters p_fead1 and p_fead2 or by parameter p_feay.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_feay` - _optional_ - Years (1 to 5) Range.  This value is used to create a date range for Formal Enforcement Actions (FEA). Used along with p_fea (which indicates whether to look within or outside of the date range) to find FEAs within (or not within) the number of years specified.
    Possible values: 1, 2, 3, 4, 5.
* `p_feaa` - _optional_ - Agency associated with Formal Enforcement Actions:
- E = EPA
- S = State
- A = All
    Possible values: A, E, S.
* `p_iea` - _optional_ - Informal Enforcement Actions [within / not within] specified date range.  The date range is determined by parameters p_iead1 and p_iead2 or by parameter p_ieay.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_ieay` - _optional_ - Years (1 to 5) Range.  This value is used to create a date range for Informal Enforcement Actions (IEA). Used along with p_iea (which indicates whether to look within or outside of the date range) to find IEAs within (or not within) the number of years specified.
    Possible values: 1, 2, 3, 4, 5.
* `p_ieaa` - _optional_ - Agency associated with Informal Enforcement Actions. If left blank, both agencies are included.
- E = EPA
- S = State
    Possible values: E, S.
* `p_qiv` - _optional_ - Quarters in Noncompliance Limiter.  Enter a coded value to limit results to facilities with given quarter of noncompliance.
- Z = Zero quarters in noncompliance.
- GEXX = Replacing XX with a numeric value, that number of quarterd or more in noncompliance.
- GTXX = Replacing XX with a numeric value, more than that number of quarters in noncompliance.
    Possible values: 0, GT1, GT2, GT4, GT8, 12.
* `p_naa` - _optional_ - Non-Attainment Area Flag.  Enter a Y or N to filter for or against facilities flagged as non-attainment areas.
* `p_impw` - _optional_ - Discharging into Impaired Waters Flag. Enter Y to limit results to facilities with discharge to waterbodies listed as impaired in the ATTAINS database.
    Possible values: Y, N.
* `p_trep` - _optional_ - Current Toxics Release Inventory (TRI) Reporter Limiter.  Enter one of the following codes to limit results.
- NONE = Never has reported to TRI.
- CURR = Current TRI reporter.
- NONCURR = Has reported to TRI in the past but not for the current reporting year.
    Possible values: NONE, CURR, NOTCURR.
* `p_tri_cat` - _optional_ - Toxic Release Inventory Released To Air Chemical Identifier Category Filter.  Enter the chemical identifier category code to limit results. Note when filtering by TRI chemical identifier categories one may not also filter by specific chemical identifiers via p_tri_pol.  You must also specify a release amount using p_tri_amt or p_tri_any_amt.
- TOTAL = Total Released to Air
- CARC = Total Carcinogens Released to Air
- HAP = Total Hazardous Air Pollutants Released to Air
    Possible values: TOTAL, CARC, HAP.
* `p_tri_amt` - _optional_ - Toxic Release Inventory Release Amount Filter.  Enter a value in pounds to limit results to facilities releasing this amount or greateer of TRI releases.  Valid values are 0, GT0, GT1000, GT5000, GT10000 and GT50000. Note when filtering by TRI release amounts one may only use either p_tri_amt or p_tri_any_amt.
    Possible values: 0, GT0, GT1000, GT5000, GT10000, GT50000.
* `p_tri_any_amt` - _optional_ - Toxic Release Inventory Release Of Any Kind Above Value Filter.  Enter a value to limit results to facilities releasing this amount or more of TRI releases.  Note when filtering by TRI releases one may only use p_tri_any_amt or p_tri_amt and not both.
* `p_tri_pol` - _optional_ - Toxic Release Inventory Chemical Identifier Filter.  Enter one or more chemical identifier codes to limit results. Note when filtering by specific TRI chemical identifiers one may not also filter by chemical identifier categories via p_tri_cat.
* `p_ghg_cat` - _optional_ - Green House Gas (GHG) Gas Code Category.  Must be used with either a formatted (p_ghg_amt) or custom (p_ghg_any_amt) release amount.
    Possible values: ALL, BIOCO2, CH4, CO2, HFC, N2O, NF3, OTHER_L, PFC, SF6.
* `p_ghg_amt` - _optional_ - Green House Gas (GHG) CO2 Equivalent Formatted Release Amount.  First 2 characters must contain GT (greater than) followed by a number.
    Possible values: None, 0, GT0, GT10000, GT25000, GT250000, GT1000000.
* `p_ghg_any_amt` - _optional_ - Green House Gas (GHG) C02 Equivalent Custom Amount.  The C02E value reported for the provided category, will be greater or equal to the amount provided.
* `p_ghg_yr` - _optional_ - Green House Gas (GHG) Reporting Year. (2010 through 2015)
* `p_nei_pol` - _optional_ - National Emissions Inventory (NEI) Pollutant Identifier.  When a pollutant identifer is entered a corresponding formatted amount or custom amount must be entered.
* `p_nei_amt` - _optional_ - National Emissions Inventory (NEI) Formatted Pollutant Amount.  A formatted value where the 1st two characters must start with GT or LT followed by a number.  Identifies facilities that have a NEI Pollutant Emission  where the supplied value is > or < the pollutant emission amount.  
    Possible values: None, 0, GT0, GT10000, GT25000, GT250000, GT1000000.
* `p_nei_any_amt` - _optional_ - National Emissions Inventory (NEI) Custom Pollutant Amount.  Only a number can be entered.  Identifies facilities with where the NEI Pollutant Emission Amount is greater than the number entered.
* `p_nei_yr` - _optional_ - National Emissions Inventory (NEI) year:  2014 or 2011
* `p_nei_cat` - _optional_ - National Emissions Inventory (NEI) Pollutant Category.  When a pollutant category is entered, a corresponding formatted pollutant amount or custom amount must be entered.
* `p_pm` - _optional_ - Percent Minority Population Limiter.  Enter a value to restrict results to facilities with a given percentage of minority population within 3-mile radius.
- NONE = 0%
- GT5 = greater than 5%
- GT10 = greater than 10%
- GT25 = greater than 25%
- GT50 = greater than 50%
- GT75 = greater than 75%
    Possible values: NONE, GT5, GT10, GT25, GT50, GT75.
* `p_pd` - _optional_ - Population Density Limiter (per sq mile). Enter a value to limit results to facilities located in area of a given population density.
- NONE = 0 population density per square mile
- GT100 = More than 100 population density per square mile
- GT500 = More than 500 population density per square mile
- GT1000 = More than 1000 population density per square mile
- GT5000 = More than 5000 population density per square mile
- GT10000 = More than 10000 population density per square mile
- GT20000 = More than 20000 population density per square mile
    Possible values: NONE, GT100, GT500, GT1000, GT5000, GT10000, GT20000.
* `p_ico` - _optional_ - Indian Country Flag.  Enter a "Y" or "N" to restrict searches to facilities inside or outside Indian Country.
    Possible values: Y, N.
* `p_huc` - _optional_ - 2-, 4-, 6-, or 8-character watershed. May contain multiple comma-separated values.
* `p_wbd` - _optional_ - 2-, 4-, 6-, 8-, 10-, or 12-character watershed (WBD from the USGS Watershed Boundary Dataset). May contain multiple comma-separated values.  Uses the FRS Best Pick Coordinate to obtain the WBD12 Huc value.
* `p_pid` - _optional_ - Nine-digit permit IDs. May contain up to 2000 comma-separated values.
* `p_med` - _optional_ - Filter Results by Media.
- M = RMP (Risk Management Plan)
- R = RCRA (Hazardous Waste)
- S = SDWA (Public Drinking Water Systems)
- W = Water
- ALL = Water and RCRA and SDWA
    Possible values: M, R, S, W, ALL.
* `p_ysl` - _optional_ - Last Facility Inspection [within / not within] Specified Date Range Indicator. The date range is determined by parameters p_idt1 and p_idt2 or by parameter p_ysly.
- W = within date range
- N = not within date range
    Possible values: W, N, NV.
* `p_ysly` - _optional_ - Number of years (1 to 5) since last facility inspection.  A value of 1 means that it has been inspected within the year.
    Possible values: 1, 2, 3, 4, 5.
* `p_ysla` - _optional_ - Facility Last Inspection Code Filter.  If left blank, both agencies are included.  Enter a value to limit results:
- E = EPA
- S = State
    Possible values: E, S, A.
* `p_stsl` - _optional_ - Last Stack Test [within / not within] Specified Date Range Indicator.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_stsly` - _optional_ - Number of years (1 to 5) since date of last stack test. A value of 1 means it has been inspected within the year.
    Possible values: 1, 2, 3, 4, 5.
* `p_stsla` - _optional_ - Stack Last Test Code Filter.  Enter a value to limit results:
- A = All
- E = EPA
- S = State
    Possible values: A, E, S.
* `p_stres` - _optional_ - Air Stack Test Status Description Filter.  Enter one or more test status descriptions to filter results.  Enter multiple values as a comma-delimited list.
* `p_sttyp` - _optional_ - Air Conductor Type Code Filter.  Enter one or more conductor type codes to filter results.  Provide multiple values as a comma-delimited list.
* `p_qs` - _optional_ - Quick Search. Allows entry for city, state, and/or zip code.
* `p_sfs` - _optional_ - Single Facility Search Filter.  Provide a facility name or program system identifier to limit results.  For the all data search, the FRS registry identifier is also searched.
* `p_tribeid` - _optional_ - Numeric code for tribe (or list of tribes).
* `p_tribename` - _optional_ - Tribe Name Filter.  Enter a single tribe name to filter results.
* `p_tribedist` - _optional_ - Proximity to tribal land limiter. Enter an amount of mile between 0 and 25 to filter results.  This parameter is only evaluated if p_tribeid is populated.
* `p_owop` - _optional_ - Owner/Operator code filter.  Enter one or more codes to limit results.
- CNG
- COR
- CTG
- DIS
- FDF
- MWD
- MXO
- NON
- POF
- SDT
- STF
- TRB
* `p_agoo` - _optional_ - Indicates whether to AND or OR the Owner/Operator parameter (p_owop) and the federal agency code (p_fa) parameters.
    Possible values: AND, OR.
* `p_idt1` - _optional_ - Beginning of date range of most recent facility inspection.
* `p_idt2` - _optional_ - End of date range of most recent facility inspection.
* `p_stdt1` - _optional_ - Beginning of date range of most recent stack test.
* `p_stdt2` - _optional_ - End of date range of most recent stack test.
* `p_pityp` - _optional_ - Inspection Type:
- CAC = Corrective Action Inspection
- CAV = Compliance Assistance Visit
- CDI = Case Development Inspection
- CEI = Inspection Inspection
- CSE = Compliance Schedule Evaluation
- FCI = Focused Compliance
- FRR = Financial Record Review
- FSD = Facility Self Disclosure
- FUI = Follow-Up Inspection
- GME = Groundwater Monitoring Evaluation
- NRR = Non-Financial Record Review
- OAM = Operation and Maintenance Inspection
May contain multiple comma-separated values.
* `p_cifdi` - _optional_ - Compliance issuess found during inspection.
    Possible values: Any, Yes, No, Undetermined.
* `p_pfead1` - _optional_ - Formal Enforcement Action Date Range Start.  Enter a date in MM/DD/YYYY format to set the start of the range for filtering by recent Formal Enforcement Action (FEA) taken against the facility within the last five years.
* `p_pfead2` - _optional_ - Formal Enforcement Action Date Range End.  Enter a date in MM/DD/YYYY format to set the end of the date range for filtering by recent Formal Enforcement Action (FEA) taken against the facility within the last five years.
* `p_pfeat` - _optional_ - Formal Enforcement Action (FEA) Code Filter.  Enter one or more three-letter FEA codes to restrict results to facilities with these attributes.  Use p_fead1 and p_fead2 parameters to further restrict this filter by entering a date range.  Provide multiple codes as a comma-delimited list.
* `p_psncq` - _optional_ - Quarters in Significant Noncompliance Limiter.  Enter a coded value to limit results to facilities with given quarter of significant noncompliance.
- Z = Zero quarters in significant noncompliance.
- GEXX = Replacing XX with a numeric value, that number of quarterd or more in significant noncompliance.
- GTXX = Replacing XX with a numeric value, more than that number of quarters in significant noncompliance.
    Possible values: GT1, GE1, GT2, GE2, GT4, GE4, GT8, GE8, GT12, GE12.
* `p_pctrack` - _optional_ - Compliance Tracking Limiter. Provide a keyword to indicate the extent to which data is being entered and effluent exceedances are being identified.
- Off
- Partial
- On
    Possible values: Off, Partial, On.
* `p_swpa` - _optional_ - Source water protection area
    Possible values: source water, surface water, ground water, waiting for SSO.
* `p_des` - _optional_ - Universe Designation Limiter.  Enter one or more universe designation codes.  Provide multiple values as a comma-delimited list.  Use code "TSDF" to return the full enforcement TSDF universe and "Operating TSDF" to return the operating TSDF universe.
* `p_fntype` - _optional_ - Controls type of text search performed on facility name with parameter p_fn.
- EXACT = Find facilities having the exact provided name(s).
- BEGINS = Find facilities with names starting with the provided term(s).
- ALL = Find facilities using Oracle text search terms.
- CONTAINS = 
    Possible values: ALL, CONTAINS, EXACT, BEGINS.
* `p_hpvmth` - _optional_ - Months in high priority violation status out of the previous three years limiter.  Provide a number of months in the past three years.  Results will limited to facilities in high priority violation status during that time. 
* `p_recvio` - _optional_ - Recent Violation Status Filter.  Enter one or more recent violation codes to limit results.  Provide multiple values as a comma-delimited list.
- NO VIOL = Selects facilities with no recent violations.
- ANY HPV = Selects facilities with either addressed or unaddressed high priority violations.
- ADDRS-EPA - Select facilities with recent EPA addressed violations.
- ADDRS-LOCAL - Select facilities with recent locally addressed violations.
- ADDRS-STATE - Select facilities with recent state addressed violations.
- UNADDR-EPA - Select facilities with recent EPA unaddressed violations.
- UNADDR-LOCAL - Select facilities with recent locally unaddressed violations.
- UNADDR-STATE - Select facilities with recent state unaddressed violations.
- FRV VIOL = Selects facilities with a recent federally reportable violation without a high priority violation.
* `p_pollvio` - _optional_ - Air Pollutant Code For A Recent Violation Filter.  Provide one or more pollutant codes to select facilities with one or more of the entered pollutant codes for a recent air violation.  Provide multiple values as a comma-delimited list.
* `p_ar` - _optional_ - Associated EPA Air Reports Program Filter.  Enter multiple values as a comma-delimited list.  Valid values are:
- TRI = Toxic Release Inventory.
- GHG = Green House Gas Reporter.
- EIS = Emission Inventory System.
- CAMD = Clean Air Markets Program Reporter.
* `p_tri_yr` - _optional_ - Toxic Release Inventory Reporting Year Filter.  Enter one or more year values to filter results by the TRI reporting year.  Provide multiple years as a comma-delimited list.
* `p_pidall` - _optional_ - Controls whether search is restricted to existing system. Y means the search will match the p_pid parameter against all associated permits (AIR, RCRA, SDWIS, etc).
    Possible values: Y, N.
* `p_fac_ico` - _optional_ - FRS tribal land code flag.  Enter "Y" or "N" to include or exclude facilities based on FRS tribal land code.
    Possible values: Y, N.
* `p_icoo` - _optional_ - Indian country search and/or flag.  Enter "Y" to set indian country search conditions to return any results found using p_ico, p_fac_ico or p_fac_icoo.  Otherwise only results matching all provided p_ico, p_fac_ico or p_fac_icoo conditions will be returned.
* `p_fac_icos` - _optional_ - FRS tribal land spatial flag.  Enter "Y" or "N" to include or exclude facilities based on FRS tribal land spatial flag.
* `p_ejscreen` - _optional_ - Enter "Y" to limit facilities to Census block groups where one of more Environmental Justice indexes above 80th percentile.
* `p_limit_addr` - _optional_ - Limit Address Search Flag.  Enter Y to restrict facility searches to native data source only.  
    Possible values: Y, N.
* `p_lat` - _optional_ - Latitude location in decimal degrees.
* `p_long` - _optional_ - Longitude location in decimal degrees.
* `p_radius` - _optional_ - Spatial Search Radius.  Enter a radius up to 100 miles in which to spatially search for facilities.
* `p_decouple` - _optional_ - Decouple Inspection Code Search Flag.  Enter "Y" to search for inspection code types with p_pityp without respect to the date range search provided with p_ysl* parameters.
    Possible values: Y, N.
* `p_ejscreen_over80cnt` - _optional_
* `queryset` - _optional_ - Query Limiter.  Enter a value to limit the number of records returned for each query. Value cannot exceed 70,000.
* `responseset` - _optional_ - Response Set Limiter. Enter a value to limit the number of records per page. Value cannot exceed 1,000.
* `tablelist` - _optional_ - Table List Flag. Enter a Y to display the first page of facility results.
    Possible values: Y, N.
* `maplist` - _optional_ - Map List Flag.  Provide a Y to return mappable coordinates representing the full geographic extent of the queryset (all facilities that met the selection criteria).
    Possible values: Y, N.
* `summarylist` - _optional_ - Summary List Flag.  Enter a Y to return a list of summary statistics based on the parameters submitted to the query service.
    Possible values: Y, N.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.

### Clean Air Act Facility Enhanced Search

> Returns either an array of Facilities or an array of Clusters that meet the specified search criteria.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
- CSV = Facility results formatted as comma delimited file download.
- GEOJSON = Facility results formatted as GeoJSON feature collection.
- GEOJSONP = Facility results formatted as GeoJSON feature collection with Padding.
- GEOJSOND = Facility results formatted as GeoJSON feature collection download.
* `p_fn` - _optional_ - Facility Name Filter. Enter one or more case-insensitive facility names to filter results.  Provide multiple values as a comma-delimited list.  See p_fntype for additional modifiers.
* `p_sa` - _optional_ - Facility street address. Enter a complete or partial street address.
* `p_sa1` - _optional_ - Facility street address. Enter a complete or partial street address.   Note that p_sa1 is culmulative with p_sa.
* `p_ct` - _optional_ - Facility City Filter. Enter a single case-insensitive city name to filter results.
* `p_co` - _optional_ - Facility County Filter. Provide a single county name in combination with a state value provided via p_st.
* `p_fips` - _optional_ - FIPS Code Filter.  Enter a single 5-character Federal Information Processing Standards (FIPS) state + county value to restrict results.  E.g. to limit results to Kenosha County, Wisconsin, use 55059.
* `p_st` - _optional_ - Facility State and State-Equivalent Filter.  Provide one or more USPS postal abbreviations for states and state-equivalents to filter results.  Provide multiple values as a comma-delimited list.
* `p_zip` - _optional_ - 5-Digit ZIP Code Filter. Provide one or more 5-digit postal zip codes to filter results.  May contain multiple comma-separated values.
* `p_lcon` - _optional_ - Air Program Local Control Region Code Filter.  Enter one or more local control region codes to filter results.  Provide multiple codes as a comma-delimited list.  Codes where they exist are specific by state.
* `p_frs` - _optional_ - Facility Registry Service ID Filter. Enter a single 12-digit FRS identifier to filter results.
* `p_reg` - _optional_ - EPA Region Filter. Provide a single value of 01 thru 10 to restrict results to a single EPA region.
    Possible values: 01, 02, 03, 04, 05, 06, 07, 08, 09, 10.
* `p_sic` - _optional_ - Standard Industrial Classification (SIC) Code Filter.  Enter a single 4-digit SIC Code to filter results.  If more complex filtering is required, use p_sic2 and p_sic4.
* `p_ncs` - _optional_ - North American Industry Classification System Filter. Enter two to six digits to filter results to facilities having matching NAICS codes.  Digits less than six will match to all codes beginning with the provided values.
* `p_qnc` - _optional_ - Number of quarters in non-compliance limiter.  Enter an integer value between 1 and 4 to limit results.
* `p_pen` - _optional_ - Last Penality Date Qualifier Filter.  Enter one of the following:   
- NEVER = No Penalties
- ANY = Any Penalty
- LEXX = Less than or equal to XX months.  Provide a number in place of XX, e.g. "LE5" for a facility with a penalty within previous 5 months.
- GTXX = Greater than XX months.  Provide a number in place of XX, eg. GT12, for a facility with the last penalty greater than 12 months ago.
* `p_opst` - _optional_ - Operating status filter.  Enter one or more operating status codes to limit results.   Provide multiple codes as a comma-delimited list.
* `xmin` - _optional_ - Minimum longitude value in decimal degrees.
* `ymin` - _optional_ - Minimum latitude value in decimal degrees.
* `xmax` - _optional_ - Maximum longitude value in decimal degrees.
* `ymax` - _optional_ - Maximum latitude value in decimal degrees.
* `p_usmex` - _optional_ - US-Mexico Border Flag.  Enter Y/N to restrict searches to facilities located within 100KM of the border.
    Possible values: Y, N.
* `p_sic2` - _optional_ - Standard Industrial Classification (SIC) Code Filter Alternate 2. Enter a wild-card search against SIC codes.  A final wild-card is always present allowing "22" to match all SIC codes beginning with 22.  Use the "%" character within strings to match any SIC values with the pattern.  For example, "2%21" matches 2021, 2121, 2221, etc.
* `p_sic4` - _optional_ - Standard Industrial Classification (SIC) Code Filter Alternate 3.  Enter the first 2, 3 or 4 SIC code digits to filter results to facilities having those code prefixes.  As this alternative does not utilize an index, p_sic2 will generally be quicker.
* `p_fa` - _optional_ - Federal Agency. 1 character or 5-character values; may contain multiple comma-separated values. ALL will retrieve all facilities where the federal agency code is not null.  Use the Federal Agencies lookup service to obtain a list of values.
* `p_act` - _optional_ - Active Permits/Facilities Flag.  Provide Y or N to filter results to facilities with active permits.
    Possible values: Y, N, A.
* `p_maj` - _optional_ - Major Facility Flag.  Enter Y to restrict results to Major facilities only.
    Possible values: Y, N.
* `p_mact` - _optional_ - CAA Maximum Achievable Control Technology (MACT) Subpart codes (alpha ID between 1 and 7 characters) applicable to the facility.
* `p_prog` - _optional_ - Air Program Code Filter.  Enter one or more Air program codes to filter results.  Provide multiple values as a comma-delimited list.
* `p_fea` - _optional_ - Formal Enforcement Actions [within / not within] specified date range indicator. The date range is determined by parameters p_fead1 and p_fead2 or by parameter p_feay.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_feay` - _optional_ - Years (1 to 5) Range.  This value is used to create a date range for Formal Enforcement Actions (FEA). Used along with p_fea (which indicates whether to look within or outside of the date range) to find FEAs within (or not within) the number of years specified.
    Possible values: 1, 2, 3, 4, 5.
* `p_feaa` - _optional_ - Agency associated with Formal Enforcement Actions:
- E = EPA
- S = State
- A = All
    Possible values: A, E, S.
* `p_iea` - _optional_ - Informal Enforcement Actions [within / not within] specified date range.  The date range is determined by parameters p_iead1 and p_iead2 or by parameter p_ieay.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_ieay` - _optional_ - Years (1 to 5) Range.  This value is used to create a date range for Informal Enforcement Actions (IEA). Used along with p_iea (which indicates whether to look within or outside of the date range) to find IEAs within (or not within) the number of years specified.
    Possible values: 1, 2, 3, 4, 5.
* `p_ieaa` - _optional_ - Agency associated with Informal Enforcement Actions. If left blank, both agencies are included.
- E = EPA
- S = State
    Possible values: E, S.
* `p_qiv` - _optional_ - Quarters in Noncompliance Limiter.  Enter a coded value to limit results to facilities with given quarter of noncompliance.
- Z = Zero quarters in noncompliance.
- GEXX = Replacing XX with a numeric value, that number of quarterd or more in noncompliance.
- GTXX = Replacing XX with a numeric value, more than that number of quarters in noncompliance.
    Possible values: 0, GT1, GT2, GT4, GT8, 12.
* `p_naa` - _optional_ - Non-Attainment Area Flag.  Enter a Y or N to filter for or against facilities flagged as non-attainment areas.
* `p_impw` - _optional_ - Discharging into Impaired Waters Flag. Enter Y to limit results to facilities with discharge to waterbodies listed as impaired in the ATTAINS database.
    Possible values: Y, N.
* `p_trep` - _optional_ - Current Toxics Release Inventory (TRI) Reporter Limiter.  Enter one of the following codes to limit results.
- NONE = Never has reported to TRI.
- CURR = Current TRI reporter.
- NONCURR = Has reported to TRI in the past but not for the current reporting year.
    Possible values: NONE, CURR, NOTCURR.
* `p_tri_cat` - _optional_ - Toxic Release Inventory Released To Air Chemical Identifier Category Filter.  Enter the chemical identifier category code to limit results. Note when filtering by TRI chemical identifier categories one may not also filter by specific chemical identifiers via p_tri_pol.  You must also specify a release amount using p_tri_amt or p_tri_any_amt.
- TOTAL = Total Released to Air
- CARC = Total Carcinogens Released to Air
- HAP = Total Hazardous Air Pollutants Released to Air
    Possible values: TOTAL, CARC, HAP.
* `p_tri_amt` - _optional_ - Toxic Release Inventory Release Amount Filter.  Enter a value in pounds to limit results to facilities releasing this amount or greateer of TRI releases.  Valid values are 0, GT0, GT1000, GT5000, GT10000 and GT50000. Note when filtering by TRI release amounts one may only use either p_tri_amt or p_tri_any_amt.
    Possible values: 0, GT0, GT1000, GT5000, GT10000, GT50000.
* `p_tri_any_amt` - _optional_ - Toxic Release Inventory Release Of Any Kind Above Value Filter.  Enter a value to limit results to facilities releasing this amount or more of TRI releases.  Note when filtering by TRI releases one may only use p_tri_any_amt or p_tri_amt and not both.
* `p_tri_pol` - _optional_ - Toxic Release Inventory Chemical Identifier Filter.  Enter one or more chemical identifier codes to limit results. Note when filtering by specific TRI chemical identifiers one may not also filter by chemical identifier categories via p_tri_cat.
* `p_ghg_cat` - _optional_ - Green House Gas (GHG) Gas Code Category.  Must be used with either a formatted (p_ghg_amt) or custom (p_ghg_any_amt) release amount.
    Possible values: ALL, BIOCO2, CH4, CO2, HFC, N2O, NF3, OTHER_L, PFC, SF6.
* `p_ghg_amt` - _optional_ - Green House Gas (GHG) CO2 Equivalent Formatted Release Amount.  First 2 characters must contain GT (greater than) followed by a number.
    Possible values: None, 0, GT0, GT10000, GT25000, GT250000, GT1000000.
* `p_ghg_any_amt` - _optional_ - Green House Gas (GHG) C02 Equivalent Custom Amount.  The C02E value reported for the provided category, will be greater or equal to the amount provided.
* `p_ghg_yr` - _optional_ - Green House Gas (GHG) Reporting Year. (2010 through 2015)
* `p_nei_pol` - _optional_ - National Emissions Inventory (NEI) Pollutant Identifier.  When a pollutant identifer is entered a corresponding formatted amount or custom amount must be entered.
* `p_nei_amt` - _optional_ - National Emissions Inventory (NEI) Formatted Pollutant Amount.  A formatted value where the 1st two characters must start with GT or LT followed by a number.  Identifies facilities that have a NEI Pollutant Emission  where the supplied value is > or < the pollutant emission amount.  
    Possible values: None, 0, GT0, GT10000, GT25000, GT250000, GT1000000.
* `p_nei_any_amt` - _optional_ - National Emissions Inventory (NEI) Custom Pollutant Amount.  Only a number can be entered.  Identifies facilities with where the NEI Pollutant Emission Amount is greater than the number entered.
* `p_nei_yr` - _optional_ - National Emissions Inventory (NEI) year:  2014 or 2011
* `p_nei_cat` - _optional_ - National Emissions Inventory (NEI) Pollutant Category.  When a pollutant category is entered, a corresponding formatted pollutant amount or custom amount must be entered.
* `p_pm` - _optional_ - Percent Minority Population Limiter.  Enter a value to restrict results to facilities with a given percentage of minority population within 3-mile radius.
- NONE = 0%
- GT5 = greater than 5%
- GT10 = greater than 10%
- GT25 = greater than 25%
- GT50 = greater than 50%
- GT75 = greater than 75%
    Possible values: NONE, GT5, GT10, GT25, GT50, GT75.
* `p_pd` - _optional_ - Population Density Limiter (per sq mile). Enter a value to limit results to facilities located in area of a given population density.
- NONE = 0 population density per square mile
- GT100 = More than 100 population density per square mile
- GT500 = More than 500 population density per square mile
- GT1000 = More than 1000 population density per square mile
- GT5000 = More than 5000 population density per square mile
- GT10000 = More than 10000 population density per square mile
- GT20000 = More than 20000 population density per square mile
    Possible values: NONE, GT100, GT500, GT1000, GT5000, GT10000, GT20000.
* `p_ico` - _optional_ - Indian Country Flag.  Enter a "Y" or "N" to restrict searches to facilities inside or outside Indian Country.
    Possible values: Y, N.
* `p_huc` - _optional_ - 2-, 4-, 6-, or 8-character watershed. May contain multiple comma-separated values.
* `p_wbd` - _optional_ - 2-, 4-, 6-, 8-, 10-, or 12-character watershed (WBD from the USGS Watershed Boundary Dataset). May contain multiple comma-separated values.  Uses the FRS Best Pick Coordinate to obtain the WBD12 Huc value.
* `p_pid` - _optional_ - Nine-digit permit IDs. May contain up to 2000 comma-separated values.
* `p_med` - _optional_ - Filter Results by Media.
- M = RMP (Risk Management Plan)
- R = RCRA (Hazardous Waste)
- S = SDWA (Public Drinking Water Systems)
- W = Water
- ALL = Water and RCRA and SDWA
    Possible values: M, R, S, W, ALL.
* `p_ysl` - _optional_ - Last Facility Inspection [within / not within] Specified Date Range Indicator. The date range is determined by parameters p_idt1 and p_idt2 or by parameter p_ysly.
- W = within date range
- N = not within date range
    Possible values: W, N, NV.
* `p_ysly` - _optional_ - Number of years (1 to 5) since last facility inspection.  A value of 1 means that it has been inspected within the year.
    Possible values: 1, 2, 3, 4, 5.
* `p_ysla` - _optional_ - Facility Last Inspection Code Filter.  If left blank, both agencies are included.  Enter a value to limit results:
- E = EPA
- S = State
    Possible values: E, S, A.
* `p_stsl` - _optional_ - Last Stack Test [within / not within] Specified Date Range Indicator.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_stsly` - _optional_ - Number of years (1 to 5) since date of last stack test. A value of 1 means it has been inspected within the year.
    Possible values: 1, 2, 3, 4, 5.
* `p_stsla` - _optional_ - Stack Last Test Code Filter.  Enter a value to limit results:
- A = All
- E = EPA
- S = State
    Possible values: A, E, S.
* `p_stres` - _optional_ - Air Stack Test Status Description Filter.  Enter one or more test status descriptions to filter results.  Enter multiple values as a comma-delimited list.
* `p_sttyp` - _optional_ - Air Conductor Type Code Filter.  Enter one or more conductor type codes to filter results.  Provide multiple values as a comma-delimited list.
* `p_qs` - _optional_ - Quick Search. Allows entry for city, state, and/or zip code.
* `p_sfs` - _optional_ - Single Facility Search Filter.  Provide a facility name or program system identifier to limit results.  For the all data search, the FRS registry identifier is also searched.
* `p_tribeid` - _optional_ - Numeric code for tribe (or list of tribes).
* `p_tribename` - _optional_ - Tribe Name Filter.  Enter a single tribe name to filter results.
* `p_tribedist` - _optional_ - Proximity to tribal land limiter. Enter an amount of mile between 0 and 25 to filter results.  This parameter is only evaluated if p_tribeid is populated.
* `p_owop` - _optional_ - Owner/Operator code filter.  Enter one or more codes to limit results.
- CNG
- COR
- CTG
- DIS
- FDF
- MWD
- MXO
- NON
- POF
- SDT
- STF
- TRB
* `p_agoo` - _optional_ - Indicates whether to AND or OR the Owner/Operator parameter (p_owop) and the federal agency code (p_fa) parameters.
    Possible values: AND, OR.
* `p_idt1` - _optional_ - Beginning of date range of most recent facility inspection.
* `p_idt2` - _optional_ - End of date range of most recent facility inspection.
* `p_stdt1` - _optional_ - Beginning of date range of most recent stack test.
* `p_stdt2` - _optional_ - End of date range of most recent stack test.
* `p_pityp` - _optional_ - Inspection Type:
- CAC = Corrective Action Inspection
- CAV = Compliance Assistance Visit
- CDI = Case Development Inspection
- CEI = Inspection Inspection
- CSE = Compliance Schedule Evaluation
- FCI = Focused Compliance
- FRR = Financial Record Review
- FSD = Facility Self Disclosure
- FUI = Follow-Up Inspection
- GME = Groundwater Monitoring Evaluation
- NRR = Non-Financial Record Review
- OAM = Operation and Maintenance Inspection
May contain multiple comma-separated values.
* `p_cifdi` - _optional_ - Compliance issuess found during inspection.
    Possible values: Any, Yes, No, Undetermined.
* `p_pfead1` - _optional_ - Formal Enforcement Action Date Range Start.  Enter a date in MM/DD/YYYY format to set the start of the range for filtering by recent Formal Enforcement Action (FEA) taken against the facility within the last five years.
* `p_pfead2` - _optional_ - Formal Enforcement Action Date Range End.  Enter a date in MM/DD/YYYY format to set the end of the date range for filtering by recent Formal Enforcement Action (FEA) taken against the facility within the last five years.
* `p_pfeat` - _optional_ - Formal Enforcement Action (FEA) Code Filter.  Enter one or more three-letter FEA codes to restrict results to facilities with these attributes.  Use p_fead1 and p_fead2 parameters to further restrict this filter by entering a date range.  Provide multiple codes as a comma-delimited list.
* `p_psncq` - _optional_ - Quarters in Significant Noncompliance Limiter.  Enter a coded value to limit results to facilities with given quarter of significant noncompliance.
- Z = Zero quarters in significant noncompliance.
- GEXX = Replacing XX with a numeric value, that number of quarterd or more in significant noncompliance.
- GTXX = Replacing XX with a numeric value, more than that number of quarters in significant noncompliance.
    Possible values: GT1, GE1, GT2, GE2, GT4, GE4, GT8, GE8, GT12, GE12.
* `p_pctrack` - _optional_ - Compliance Tracking Limiter. Provide a keyword to indicate the extent to which data is being entered and effluent exceedances are being identified.
- Off
- Partial
- On
    Possible values: Off, Partial, On.
* `p_swpa` - _optional_ - Source water protection area
    Possible values: source water, surface water, ground water, waiting for SSO.
* `p_des` - _optional_ - Universe Designation Limiter.  Enter one or more universe designation codes.  Provide multiple values as a comma-delimited list.  Use code "TSDF" to return the full enforcement TSDF universe and "Operating TSDF" to return the operating TSDF universe.
* `p_fntype` - _optional_ - Controls type of text search performed on facility name with parameter p_fn.
- EXACT = Find facilities having the exact provided name(s).
- BEGINS = Find facilities with names starting with the provided term(s).
- ALL = Find facilities using Oracle text search terms.
- CONTAINS = 
    Possible values: ALL, CONTAINS, EXACT, BEGINS.
* `p_hpvmth` - _optional_ - Months in high priority violation status out of the previous three years limiter.  Provide a number of months in the past three years.  Results will limited to facilities in high priority violation status during that time. 
* `p_recvio` - _optional_ - Recent Violation Status Filter.  Enter one or more recent violation codes to limit results.  Provide multiple values as a comma-delimited list.
- NO VIOL = Selects facilities with no recent violations.
- ANY HPV = Selects facilities with either addressed or unaddressed high priority violations.
- ADDRS-EPA - Select facilities with recent EPA addressed violations.
- ADDRS-LOCAL - Select facilities with recent locally addressed violations.
- ADDRS-STATE - Select facilities with recent state addressed violations.
- UNADDR-EPA - Select facilities with recent EPA unaddressed violations.
- UNADDR-LOCAL - Select facilities with recent locally unaddressed violations.
- UNADDR-STATE - Select facilities with recent state unaddressed violations.
- FRV VIOL = Selects facilities with a recent federally reportable violation without a high priority violation.
* `p_pollvio` - _optional_ - Air Pollutant Code For A Recent Violation Filter.  Provide one or more pollutant codes to select facilities with one or more of the entered pollutant codes for a recent air violation.  Provide multiple values as a comma-delimited list.
* `p_ar` - _optional_ - Associated EPA Air Reports Program Filter.  Enter multiple values as a comma-delimited list.  Valid values are:
- TRI = Toxic Release Inventory.
- GHG = Green House Gas Reporter.
- EIS = Emission Inventory System.
- CAMD = Clean Air Markets Program Reporter.
* `p_tri_yr` - _optional_ - Toxic Release Inventory Reporting Year Filter.  Enter one or more year values to filter results by the TRI reporting year.  Provide multiple years as a comma-delimited list.
* `p_pidall` - _optional_ - Controls whether search is restricted to existing system. Y means the search will match the p_pid parameter against all associated permits (AIR, RCRA, SDWIS, etc).
    Possible values: Y, N.
* `p_fac_ico` - _optional_ - FRS tribal land code flag.  Enter "Y" or "N" to include or exclude facilities based on FRS tribal land code.
    Possible values: Y, N.
* `p_icoo` - _optional_ - Indian country search and/or flag.  Enter "Y" to set indian country search conditions to return any results found using p_ico, p_fac_ico or p_fac_icoo.  Otherwise only results matching all provided p_ico, p_fac_ico or p_fac_icoo conditions will be returned.
* `p_fac_icos` - _optional_ - FRS tribal land spatial flag.  Enter "Y" or "N" to include or exclude facilities based on FRS tribal land spatial flag.
* `p_ejscreen` - _optional_ - Enter "Y" to limit facilities to Census block groups where one of more Environmental Justice indexes above 80th percentile.
* `p_limit_addr` - _optional_ - Limit Address Search Flag.  Enter Y to restrict facility searches to native data source only.  
    Possible values: Y, N.
* `p_lat` - _optional_ - Latitude location in decimal degrees.
* `p_long` - _optional_ - Longitude location in decimal degrees.
* `p_radius` - _optional_ - Spatial Search Radius.  Enter a radius up to 100 miles in which to spatially search for facilities.
* `p_decouple` - _optional_ - Decouple Inspection Code Search Flag.  Enter "Y" to search for inspection code types with p_pityp without respect to the date range search provided with p_ysl* parameters.
    Possible values: Y, N.
* `p_ejscreen_over80cnt` - _optional_
* `queryset` - _optional_ - Query Limiter.  Enter a value to limit the number of records returned for each query. Value cannot exceed 70,000.
* `responseset` - _optional_ - Response Set Limiter. Enter a value to limit the number of records per page. Value cannot exceed 1,000.
* `summarylist` - _optional_ - Summary List Flag.  Enter a Y to return a list of summary statistics based on the parameters submitted to the query service.
    Possible values: Y, N.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.
* `p_pretty_print` - _optional_ - Optional flag to request GeoJSON formatted results to be pretty printed.  Only provide a numeric value when the output needs to be human readable as pretty printing has a performance cost.

### Clean Air Act Facility Enhanced Search

> Returns either an array of Facilities or an array of Clusters that meet the specified search criteria.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
- CSV = Facility results formatted as comma delimited file download.
- GEOJSON = Facility results formatted as GeoJSON feature collection.
- GEOJSONP = Facility results formatted as GeoJSON feature collection with Padding.
- GEOJSOND = Facility results formatted as GeoJSON feature collection download.
* `p_fn` - _optional_ - Facility Name Filter. Enter one or more case-insensitive facility names to filter results.  Provide multiple values as a comma-delimited list.  See p_fntype for additional modifiers.
* `p_sa` - _optional_ - Facility street address. Enter a complete or partial street address.
* `p_sa1` - _optional_ - Facility street address. Enter a complete or partial street address.   Note that p_sa1 is culmulative with p_sa.
* `p_ct` - _optional_ - Facility City Filter. Enter a single case-insensitive city name to filter results.
* `p_co` - _optional_ - Facility County Filter. Provide a single county name in combination with a state value provided via p_st.
* `p_fips` - _optional_ - FIPS Code Filter.  Enter a single 5-character Federal Information Processing Standards (FIPS) state + county value to restrict results.  E.g. to limit results to Kenosha County, Wisconsin, use 55059.
* `p_st` - _optional_ - Facility State and State-Equivalent Filter.  Provide one or more USPS postal abbreviations for states and state-equivalents to filter results.  Provide multiple values as a comma-delimited list.
* `p_zip` - _optional_ - 5-Digit ZIP Code Filter. Provide one or more 5-digit postal zip codes to filter results.  May contain multiple comma-separated values.
* `p_lcon` - _optional_ - Air Program Local Control Region Code Filter.  Enter one or more local control region codes to filter results.  Provide multiple codes as a comma-delimited list.  Codes where they exist are specific by state.
* `p_frs` - _optional_ - Facility Registry Service ID Filter. Enter a single 12-digit FRS identifier to filter results.
* `p_reg` - _optional_ - EPA Region Filter. Provide a single value of 01 thru 10 to restrict results to a single EPA region.
    Possible values: 01, 02, 03, 04, 05, 06, 07, 08, 09, 10.
* `p_sic` - _optional_ - Standard Industrial Classification (SIC) Code Filter.  Enter a single 4-digit SIC Code to filter results.  If more complex filtering is required, use p_sic2 and p_sic4.
* `p_ncs` - _optional_ - North American Industry Classification System Filter. Enter two to six digits to filter results to facilities having matching NAICS codes.  Digits less than six will match to all codes beginning with the provided values.
* `p_qnc` - _optional_ - Number of quarters in non-compliance limiter.  Enter an integer value between 1 and 4 to limit results.
* `p_pen` - _optional_ - Last Penality Date Qualifier Filter.  Enter one of the following:   
- NEVER = No Penalties
- ANY = Any Penalty
- LEXX = Less than or equal to XX months.  Provide a number in place of XX, e.g. "LE5" for a facility with a penalty within previous 5 months.
- GTXX = Greater than XX months.  Provide a number in place of XX, eg. GT12, for a facility with the last penalty greater than 12 months ago.
* `p_opst` - _optional_ - Operating status filter.  Enter one or more operating status codes to limit results.   Provide multiple codes as a comma-delimited list.
* `xmin` - _optional_ - Minimum longitude value in decimal degrees.
* `ymin` - _optional_ - Minimum latitude value in decimal degrees.
* `xmax` - _optional_ - Maximum longitude value in decimal degrees.
* `ymax` - _optional_ - Maximum latitude value in decimal degrees.
* `p_usmex` - _optional_ - US-Mexico Border Flag.  Enter Y/N to restrict searches to facilities located within 100KM of the border.
    Possible values: Y, N.
* `p_sic2` - _optional_ - Standard Industrial Classification (SIC) Code Filter Alternate 2. Enter a wild-card search against SIC codes.  A final wild-card is always present allowing "22" to match all SIC codes beginning with 22.  Use the "%" character within strings to match any SIC values with the pattern.  For example, "2%21" matches 2021, 2121, 2221, etc.
* `p_sic4` - _optional_ - Standard Industrial Classification (SIC) Code Filter Alternate 3.  Enter the first 2, 3 or 4 SIC code digits to filter results to facilities having those code prefixes.  As this alternative does not utilize an index, p_sic2 will generally be quicker.
* `p_fa` - _optional_ - Federal Agency. 1 character or 5-character values; may contain multiple comma-separated values. ALL will retrieve all facilities where the federal agency code is not null.  Use the Federal Agencies lookup service to obtain a list of values.
* `p_act` - _optional_ - Active Permits/Facilities Flag.  Provide Y or N to filter results to facilities with active permits.
    Possible values: Y, N, A.
* `p_maj` - _optional_ - Major Facility Flag.  Enter Y to restrict results to Major facilities only.
    Possible values: Y, N.
* `p_mact` - _optional_ - CAA Maximum Achievable Control Technology (MACT) Subpart codes (alpha ID between 1 and 7 characters) applicable to the facility.
* `p_prog` - _optional_ - Air Program Code Filter.  Enter one or more Air program codes to filter results.  Provide multiple values as a comma-delimited list.
* `p_fea` - _optional_ - Formal Enforcement Actions [within / not within] specified date range indicator. The date range is determined by parameters p_fead1 and p_fead2 or by parameter p_feay.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_feay` - _optional_ - Years (1 to 5) Range.  This value is used to create a date range for Formal Enforcement Actions (FEA). Used along with p_fea (which indicates whether to look within or outside of the date range) to find FEAs within (or not within) the number of years specified.
    Possible values: 1, 2, 3, 4, 5.
* `p_feaa` - _optional_ - Agency associated with Formal Enforcement Actions:
- E = EPA
- S = State
- A = All
    Possible values: A, E, S.
* `p_iea` - _optional_ - Informal Enforcement Actions [within / not within] specified date range.  The date range is determined by parameters p_iead1 and p_iead2 or by parameter p_ieay.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_ieay` - _optional_ - Years (1 to 5) Range.  This value is used to create a date range for Informal Enforcement Actions (IEA). Used along with p_iea (which indicates whether to look within or outside of the date range) to find IEAs within (or not within) the number of years specified.
    Possible values: 1, 2, 3, 4, 5.
* `p_ieaa` - _optional_ - Agency associated with Informal Enforcement Actions. If left blank, both agencies are included.
- E = EPA
- S = State
    Possible values: E, S.
* `p_qiv` - _optional_ - Quarters in Noncompliance Limiter.  Enter a coded value to limit results to facilities with given quarter of noncompliance.
- Z = Zero quarters in noncompliance.
- GEXX = Replacing XX with a numeric value, that number of quarterd or more in noncompliance.
- GTXX = Replacing XX with a numeric value, more than that number of quarters in noncompliance.
    Possible values: 0, GT1, GT2, GT4, GT8, 12.
* `p_naa` - _optional_ - Non-Attainment Area Flag.  Enter a Y or N to filter for or against facilities flagged as non-attainment areas.
* `p_impw` - _optional_ - Discharging into Impaired Waters Flag. Enter Y to limit results to facilities with discharge to waterbodies listed as impaired in the ATTAINS database.
    Possible values: Y, N.
* `p_trep` - _optional_ - Current Toxics Release Inventory (TRI) Reporter Limiter.  Enter one of the following codes to limit results.
- NONE = Never has reported to TRI.
- CURR = Current TRI reporter.
- NONCURR = Has reported to TRI in the past but not for the current reporting year.
    Possible values: NONE, CURR, NOTCURR.
* `p_tri_cat` - _optional_ - Toxic Release Inventory Released To Air Chemical Identifier Category Filter.  Enter the chemical identifier category code to limit results. Note when filtering by TRI chemical identifier categories one may not also filter by specific chemical identifiers via p_tri_pol.  You must also specify a release amount using p_tri_amt or p_tri_any_amt.
- TOTAL = Total Released to Air
- CARC = Total Carcinogens Released to Air
- HAP = Total Hazardous Air Pollutants Released to Air
    Possible values: TOTAL, CARC, HAP.
* `p_tri_amt` - _optional_ - Toxic Release Inventory Release Amount Filter.  Enter a value in pounds to limit results to facilities releasing this amount or greateer of TRI releases.  Valid values are 0, GT0, GT1000, GT5000, GT10000 and GT50000. Note when filtering by TRI release amounts one may only use either p_tri_amt or p_tri_any_amt.
    Possible values: 0, GT0, GT1000, GT5000, GT10000, GT50000.
* `p_tri_any_amt` - _optional_ - Toxic Release Inventory Release Of Any Kind Above Value Filter.  Enter a value to limit results to facilities releasing this amount or more of TRI releases.  Note when filtering by TRI releases one may only use p_tri_any_amt or p_tri_amt and not both.
* `p_tri_pol` - _optional_ - Toxic Release Inventory Chemical Identifier Filter.  Enter one or more chemical identifier codes to limit results. Note when filtering by specific TRI chemical identifiers one may not also filter by chemical identifier categories via p_tri_cat.
* `p_ghg_cat` - _optional_ - Green House Gas (GHG) Gas Code Category.  Must be used with either a formatted (p_ghg_amt) or custom (p_ghg_any_amt) release amount.
    Possible values: ALL, BIOCO2, CH4, CO2, HFC, N2O, NF3, OTHER_L, PFC, SF6.
* `p_ghg_amt` - _optional_ - Green House Gas (GHG) CO2 Equivalent Formatted Release Amount.  First 2 characters must contain GT (greater than) followed by a number.
    Possible values: None, 0, GT0, GT10000, GT25000, GT250000, GT1000000.
* `p_ghg_any_amt` - _optional_ - Green House Gas (GHG) C02 Equivalent Custom Amount.  The C02E value reported for the provided category, will be greater or equal to the amount provided.
* `p_ghg_yr` - _optional_ - Green House Gas (GHG) Reporting Year. (2010 through 2015)
* `p_nei_pol` - _optional_ - National Emissions Inventory (NEI) Pollutant Identifier.  When a pollutant identifer is entered a corresponding formatted amount or custom amount must be entered.
* `p_nei_amt` - _optional_ - National Emissions Inventory (NEI) Formatted Pollutant Amount.  A formatted value where the 1st two characters must start with GT or LT followed by a number.  Identifies facilities that have a NEI Pollutant Emission  where the supplied value is > or < the pollutant emission amount.  
    Possible values: None, 0, GT0, GT10000, GT25000, GT250000, GT1000000.
* `p_nei_any_amt` - _optional_ - National Emissions Inventory (NEI) Custom Pollutant Amount.  Only a number can be entered.  Identifies facilities with where the NEI Pollutant Emission Amount is greater than the number entered.
* `p_nei_yr` - _optional_ - National Emissions Inventory (NEI) year:  2014 or 2011
* `p_nei_cat` - _optional_ - National Emissions Inventory (NEI) Pollutant Category.  When a pollutant category is entered, a corresponding formatted pollutant amount or custom amount must be entered.
* `p_pm` - _optional_ - Percent Minority Population Limiter.  Enter a value to restrict results to facilities with a given percentage of minority population within 3-mile radius.
- NONE = 0%
- GT5 = greater than 5%
- GT10 = greater than 10%
- GT25 = greater than 25%
- GT50 = greater than 50%
- GT75 = greater than 75%
    Possible values: NONE, GT5, GT10, GT25, GT50, GT75.
* `p_pd` - _optional_ - Population Density Limiter (per sq mile). Enter a value to limit results to facilities located in area of a given population density.
- NONE = 0 population density per square mile
- GT100 = More than 100 population density per square mile
- GT500 = More than 500 population density per square mile
- GT1000 = More than 1000 population density per square mile
- GT5000 = More than 5000 population density per square mile
- GT10000 = More than 10000 population density per square mile
- GT20000 = More than 20000 population density per square mile
    Possible values: NONE, GT100, GT500, GT1000, GT5000, GT10000, GT20000.
* `p_ico` - _optional_ - Indian Country Flag.  Enter a "Y" or "N" to restrict searches to facilities inside or outside Indian Country.
    Possible values: Y, N.
* `p_huc` - _optional_ - 2-, 4-, 6-, or 8-character watershed. May contain multiple comma-separated values.
* `p_wbd` - _optional_ - 2-, 4-, 6-, 8-, 10-, or 12-character watershed (WBD from the USGS Watershed Boundary Dataset). May contain multiple comma-separated values.  Uses the FRS Best Pick Coordinate to obtain the WBD12 Huc value.
* `p_pid` - _optional_ - Nine-digit permit IDs. May contain up to 2000 comma-separated values.
* `p_med` - _optional_ - Filter Results by Media.
- M = RMP (Risk Management Plan)
- R = RCRA (Hazardous Waste)
- S = SDWA (Public Drinking Water Systems)
- W = Water
- ALL = Water and RCRA and SDWA
    Possible values: M, R, S, W, ALL.
* `p_ysl` - _optional_ - Last Facility Inspection [within / not within] Specified Date Range Indicator. The date range is determined by parameters p_idt1 and p_idt2 or by parameter p_ysly.
- W = within date range
- N = not within date range
    Possible values: W, N, NV.
* `p_ysly` - _optional_ - Number of years (1 to 5) since last facility inspection.  A value of 1 means that it has been inspected within the year.
    Possible values: 1, 2, 3, 4, 5.
* `p_ysla` - _optional_ - Facility Last Inspection Code Filter.  If left blank, both agencies are included.  Enter a value to limit results:
- E = EPA
- S = State
    Possible values: E, S, A.
* `p_stsl` - _optional_ - Last Stack Test [within / not within] Specified Date Range Indicator.
- W = within date range
- N = not within date range
    Possible values: W, N.
* `p_stsly` - _optional_ - Number of years (1 to 5) since date of last stack test. A value of 1 means it has been inspected within the year.
    Possible values: 1, 2, 3, 4, 5.
* `p_stsla` - _optional_ - Stack Last Test Code Filter.  Enter a value to limit results:
- A = All
- E = EPA
- S = State
    Possible values: A, E, S.
* `p_stres` - _optional_ - Air Stack Test Status Description Filter.  Enter one or more test status descriptions to filter results.  Enter multiple values as a comma-delimited list.
* `p_sttyp` - _optional_ - Air Conductor Type Code Filter.  Enter one or more conductor type codes to filter results.  Provide multiple values as a comma-delimited list.
* `p_qs` - _optional_ - Quick Search. Allows entry for city, state, and/or zip code.
* `p_sfs` - _optional_ - Single Facility Search Filter.  Provide a facility name or program system identifier to limit results.  For the all data search, the FRS registry identifier is also searched.
* `p_tribeid` - _optional_ - Numeric code for tribe (or list of tribes).
* `p_tribename` - _optional_ - Tribe Name Filter.  Enter a single tribe name to filter results.
* `p_tribedist` - _optional_ - Proximity to tribal land limiter. Enter an amount of mile between 0 and 25 to filter results.  This parameter is only evaluated if p_tribeid is populated.
* `p_owop` - _optional_ - Owner/Operator code filter.  Enter one or more codes to limit results.
- CNG
- COR
- CTG
- DIS
- FDF
- MWD
- MXO
- NON
- POF
- SDT
- STF
- TRB
* `p_agoo` - _optional_ - Indicates whether to AND or OR the Owner/Operator parameter (p_owop) and the federal agency code (p_fa) parameters.
    Possible values: AND, OR.
* `p_idt1` - _optional_ - Beginning of date range of most recent facility inspection.
* `p_idt2` - _optional_ - End of date range of most recent facility inspection.
* `p_stdt1` - _optional_ - Beginning of date range of most recent stack test.
* `p_stdt2` - _optional_ - End of date range of most recent stack test.
* `p_pityp` - _optional_ - Inspection Type:
- CAC = Corrective Action Inspection
- CAV = Compliance Assistance Visit
- CDI = Case Development Inspection
- CEI = Inspection Inspection
- CSE = Compliance Schedule Evaluation
- FCI = Focused Compliance
- FRR = Financial Record Review
- FSD = Facility Self Disclosure
- FUI = Follow-Up Inspection
- GME = Groundwater Monitoring Evaluation
- NRR = Non-Financial Record Review
- OAM = Operation and Maintenance Inspection
May contain multiple comma-separated values.
* `p_cifdi` - _optional_ - Compliance issuess found during inspection.
    Possible values: Any, Yes, No, Undetermined.
* `p_pfead1` - _optional_ - Formal Enforcement Action Date Range Start.  Enter a date in MM/DD/YYYY format to set the start of the range for filtering by recent Formal Enforcement Action (FEA) taken against the facility within the last five years.
* `p_pfead2` - _optional_ - Formal Enforcement Action Date Range End.  Enter a date in MM/DD/YYYY format to set the end of the date range for filtering by recent Formal Enforcement Action (FEA) taken against the facility within the last five years.
* `p_pfeat` - _optional_ - Formal Enforcement Action (FEA) Code Filter.  Enter one or more three-letter FEA codes to restrict results to facilities with these attributes.  Use p_fead1 and p_fead2 parameters to further restrict this filter by entering a date range.  Provide multiple codes as a comma-delimited list.
* `p_psncq` - _optional_ - Quarters in Significant Noncompliance Limiter.  Enter a coded value to limit results to facilities with given quarter of significant noncompliance.
- Z = Zero quarters in significant noncompliance.
- GEXX = Replacing XX with a numeric value, that number of quarterd or more in significant noncompliance.
- GTXX = Replacing XX with a numeric value, more than that number of quarters in significant noncompliance.
    Possible values: GT1, GE1, GT2, GE2, GT4, GE4, GT8, GE8, GT12, GE12.
* `p_pctrack` - _optional_ - Compliance Tracking Limiter. Provide a keyword to indicate the extent to which data is being entered and effluent exceedances are being identified.
- Off
- Partial
- On
    Possible values: Off, Partial, On.
* `p_swpa` - _optional_ - Source water protection area
    Possible values: source water, surface water, ground water, waiting for SSO.
* `p_des` - _optional_ - Universe Designation Limiter.  Enter one or more universe designation codes.  Provide multiple values as a comma-delimited list.  Use code "TSDF" to return the full enforcement TSDF universe and "Operating TSDF" to return the operating TSDF universe.
* `p_fntype` - _optional_ - Controls type of text search performed on facility name with parameter p_fn.
- EXACT = Find facilities having the exact provided name(s).
- BEGINS = Find facilities with names starting with the provided term(s).
- ALL = Find facilities using Oracle text search terms.
- CONTAINS = 
    Possible values: ALL, CONTAINS, EXACT, BEGINS.
* `p_hpvmth` - _optional_ - Months in high priority violation status out of the previous three years limiter.  Provide a number of months in the past three years.  Results will limited to facilities in high priority violation status during that time. 
* `p_recvio` - _optional_ - Recent Violation Status Filter.  Enter one or more recent violation codes to limit results.  Provide multiple values as a comma-delimited list.
- NO VIOL = Selects facilities with no recent violations.
- ANY HPV = Selects facilities with either addressed or unaddressed high priority violations.
- ADDRS-EPA - Select facilities with recent EPA addressed violations.
- ADDRS-LOCAL - Select facilities with recent locally addressed violations.
- ADDRS-STATE - Select facilities with recent state addressed violations.
- UNADDR-EPA - Select facilities with recent EPA unaddressed violations.
- UNADDR-LOCAL - Select facilities with recent locally unaddressed violations.
- UNADDR-STATE - Select facilities with recent state unaddressed violations.
- FRV VIOL = Selects facilities with a recent federally reportable violation without a high priority violation.
* `p_pollvio` - _optional_ - Air Pollutant Code For A Recent Violation Filter.  Provide one or more pollutant codes to select facilities with one or more of the entered pollutant codes for a recent air violation.  Provide multiple values as a comma-delimited list.
* `p_ar` - _optional_ - Associated EPA Air Reports Program Filter.  Enter multiple values as a comma-delimited list.  Valid values are:
- TRI = Toxic Release Inventory.
- GHG = Green House Gas Reporter.
- EIS = Emission Inventory System.
- CAMD = Clean Air Markets Program Reporter.
* `p_tri_yr` - _optional_ - Toxic Release Inventory Reporting Year Filter.  Enter one or more year values to filter results by the TRI reporting year.  Provide multiple years as a comma-delimited list.
* `p_pidall` - _optional_ - Controls whether search is restricted to existing system. Y means the search will match the p_pid parameter against all associated permits (AIR, RCRA, SDWIS, etc).
    Possible values: Y, N.
* `p_fac_ico` - _optional_ - FRS tribal land code flag.  Enter "Y" or "N" to include or exclude facilities based on FRS tribal land code.
    Possible values: Y, N.
* `p_icoo` - _optional_ - Indian country search and/or flag.  Enter "Y" to set indian country search conditions to return any results found using p_ico, p_fac_ico or p_fac_icoo.  Otherwise only results matching all provided p_ico, p_fac_ico or p_fac_icoo conditions will be returned.
* `p_fac_icos` - _optional_ - FRS tribal land spatial flag.  Enter "Y" or "N" to include or exclude facilities based on FRS tribal land spatial flag.
* `p_ejscreen` - _optional_ - Enter "Y" to limit facilities to Census block groups where one of more Environmental Justice indexes above 80th percentile.
* `p_limit_addr` - _optional_ - Limit Address Search Flag.  Enter Y to restrict facility searches to native data source only.  
    Possible values: Y, N.
* `p_lat` - _optional_ - Latitude location in decimal degrees.
* `p_long` - _optional_ - Longitude location in decimal degrees.
* `p_radius` - _optional_ - Spatial Search Radius.  Enter a radius up to 100 miles in which to spatially search for facilities.
* `p_decouple` - _optional_ - Decouple Inspection Code Search Flag.  Enter "Y" to search for inspection code types with p_pityp without respect to the date range search provided with p_ysl* parameters.
    Possible values: Y, N.
* `p_ejscreen_over80cnt` - _optional_
* `queryset` - _optional_ - Query Limiter.  Enter a value to limit the number of records returned for each query. Value cannot exceed 70,000.
* `responseset` - _optional_ - Response Set Limiter. Enter a value to limit the number of records per page. Value cannot exceed 1,000.
* `summarylist` - _optional_ - Summary List Flag.  Enter a Y to return a list of summary statistics based on the parameters submitted to the query service.
    Possible values: Y, N.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.
* `p_pretty_print` - _optional_ - Optional flag to request GeoJSON formatted results to be pretty printed.  Only provide a numeric value when the output needs to be human readable as pretty printing has a performance cost.

### Clean Air Act GeoJSON Service

> Based on the QID obtained from a get_facilities or get_facility_info query, return GeoJSON of the facilities found.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- GEOJSON = Facility results formatted as GeoJSON feature collection (default).
- GEOJSONP = Facility results formatted as GeoJSON feature collection with Padding.
- GEOJSOND = Facility results formatted as GeoJSON feature collection download.
* `qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `newsort` - _optional_ - Output Sort Column.  Enter the number of the column on which the data will be sorted. If unpopulated results will sort on the first column.
* `descending` - _optional_ - Output Sort Column Descending Flag.  Enter Y to column identified in the newsort parameter descending.  Enter N to use ascending sort order. Used only when newsort parameter is populated.
    Possible values: Y, N.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.
* `p_pretty_print` - _optional_ - Optional flag to request GeoJSON formatted results to be pretty printed.  Only provide a numeric value when the output needs to be human readable as pretty printing has a performance cost.

### Clean Air Act GeoJSON Service

> Based on the QID obtained from a get_facilities or get_facility_info query, return GeoJSON of the facilities found.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- GEOJSON = Facility results formatted as GeoJSON feature collection (default).
- GEOJSONP = Facility results formatted as GeoJSON feature collection with Padding.
- GEOJSOND = Facility results formatted as GeoJSON feature collection download.
* `qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `newsort` - _optional_ - Output Sort Column.  Enter the number of the column on which the data will be sorted. If unpopulated results will sort on the first column.
* `descending` - _optional_ - Output Sort Column Descending Flag.  Enter Y to column identified in the newsort parameter descending.  Enter N to use ascending sort order. Used only when newsort parameter is populated.
    Possible values: Y, N.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.
* `p_pretty_print` - _optional_ - Optional flag to request GeoJSON formatted results to be pretty printed.  Only provide a numeric value when the output needs to be human readable as pretty printing has a performance cost.

### Clean Air Act Info Clusters Service

> Based on the QID obtained from a clustered get_facility_info query, download cluster facility information as either a CSV or GEOJSON file.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- CSV = Facility results formatted as comma delimited file download (default).
- GEOJSOND = Facility results formatted as GeoJSON feature collection download.
* `p_qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `p_pretty_print` - _optional_ - Optional flag to request GeoJSON formatted results to be pretty printed.  Only provide a numeric value when the output needs to be human readable as pretty printing has a performance cost.

### Clean Air Act Info Clusters Service

> Based on the QID obtained from a clustered get_facility_info query, download cluster facility information as either a CSV or GEOJSON file.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- CSV = Facility results formatted as comma delimited file download (default).
- GEOJSOND = Facility results formatted as GeoJSON feature collection download.
* `p_qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `p_pretty_print` - _optional_ - Optional flag to request GeoJSON formatted results to be pretty printed.  Only provide a numeric value when the output needs to be human readable as pretty printing has a performance cost.

### Clean Air Act Map Service

> The purpose of the GET_MAP service is to display facility coordinates and facility clusters related to a get_facilities facility query. Currently, the maximum number of coordinates returned is 500. GET_MAP performs automatic clustering at the state, county, and zip code levels to maximize the number of coordinates returned.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
    Possible values: JSONP, JSON, XML.
* `qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `tablelist` - _optional_ - Table List Flag. Enter a Y to display the first page of facility results.
    Possible values: Y, N.
* `c1_lat` - _optional_ - Latitude of 1st corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `c1_long` - _optional_ - Longitude of 1st corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `c2_lat` - _optional_ - Latitude of 2nd corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `c2_long` - _optional_ - Longitude of 2nd corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_id` - _required_ - Identifier for the service.

### Clean Air Act Map Service

> The purpose of the GET_MAP service is to display facility coordinates and facility clusters related to a get_facilities facility query. Currently, the maximum number of coordinates returned is 500. GET_MAP performs automatic clustering at the state, county, and zip code levels to maximize the number of coordinates returned.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
    Possible values: JSONP, JSON, XML.
* `qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `tablelist` - _optional_ - Table List Flag. Enter a Y to display the first page of facility results.
    Possible values: Y, N.
* `c1_lat` - _optional_ - Latitude of 1st corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `c1_long` - _optional_ - Longitude of 1st corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `c2_lat` - _optional_ - Latitude of 2nd corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `c2_long` - _optional_ - Longitude of 2nd corner of box that bounds the resulting facilities. The latitude and longitude of both corners of the bounding box must be provided.
* `p_id` - _required_ - Identifier for the service.

### Clean Air Act Search by Query ID

> GET_QID is passed with a query ID corresponding to a previously run get_facilities query. It then returns a Facility object containing all matching facilities. The main purpose of GET_QID is for large querysets that contain multiple pages (responsesets) of output. GET_QID allows for pagination and for the selection and sorting of columns.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
    Possible values: JSONP, JSON, XML.
* `qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `pageno` - _optional_ - Indicates the number of the page to display. It is used only when the results are paginated.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `newsort` - _optional_ - Output Sort Column.  Enter the number of the column on which the data will be sorted. If unpopulated results will sort on the first column.
* `descending` - _optional_ - Output Sort Column Descending Flag.  Enter Y to column identified in the newsort parameter descending.  Enter N to use ascending sort order. Used only when newsort parameter is populated.
    Possible values: Y, N.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.

### Clean Air Act Search by Query ID

> GET_QID is passed with a query ID corresponding to a previously run get_facilities query. It then returns a Facility object containing all matching facilities. The main purpose of GET_QID is for large querysets that contain multiple pages (responsesets) of output. GET_QID allows for pagination and for the selection and sorting of columns.

*Tags:* `Facilities`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
    Possible values: JSONP, JSON, XML.
* `qid` - _required_ - Query ID Selector.  Enter the QueryID number from a previously run query.
* `pageno` - _optional_ - Indicates the number of the page to display. It is used only when the results are paginated.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.
* `newsort` - _optional_ - Output Sort Column.  Enter the number of the column on which the data will be sorted. If unpopulated results will sort on the first column.
* `descending` - _optional_ - Output Sort Column Descending Flag.  Enter Y to column identified in the newsort parameter descending.  Enter N to use ascending sort order. Used only when newsort parameter is populated.
    Possible values: Y, N.
* `qcolumns` - _optional_ - Used to cutomize service output.  A list of comma-separated column IDs of output objects that will be returned in the service query object or download.  Use the metadata service endpoint for a complete list of Ids and definitions.

### Clean Air Act Metadata Service

> Returns the JSON Object Name and ColumnId for usage with the qcolumns parameter for get_qid, get_facility_info and other service endpoints.

*Tags:* `Metadata`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
    Possible values: JSONP, JSON, XML.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.

### Clean Air Act Metadata Service

> Returns the JSON Object Name and ColumnId for usage with the qcolumns parameter for get_qid, get_facility_info and other service endpoints.

*Tags:* `Metadata`

#### Input Parameters
* `output` - _optional_ - Output Format Flag.  Enter one of the following keywords:
- JSON = Data model formatted as Javascript Object Notation (default).
- JSONP = Data model formatted as Javascript Object Notation with Padding.  
- XML = Data model formatted as Extensible Markup Language.
    Possible values: JSONP, JSON, XML.
* `callback` - _optional_ - JSONP Callback.  For use with JSONP and GEOJSONP output only.  Enter a name of the function in which to wrap the JSON response.

## License

**flow**ground :- Telekom iPaaS / epa-gov-air-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
