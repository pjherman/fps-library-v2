# UPGRADE FROM v1.0 to v1.1 DO's:
    advancedContent:      Copy latest advanced for console params
    panelVersionNumber:   Update analytics, main webpart component to use version from about
    siteThemes:           Remove siteThemes from FetchBannerX in main react component.  add this._fpsSiteThemes = stylesFPS to main react
    Gulp file:            Update Gulp file to add Date to WebPackAnalyzer
    OnInit:               add to onInit:  _analyticsListX, _analyticsOptionsX, _allowPropsEasyMode, _wpInfoGroupExpanded, _panelVersion
    Local Installs:       remove local install of @mikezimm/fps-styles (found this in drilldown)

# Publish hints:

npm run clean
npm run build
npm version major/minor/patch
npm publish --access=public
npm install @mikezimm/fps-library-v2@1.1.79

# Changelog
NOTE:  TURN BACK ON STRICT NULL CHECKS - turned off for PropPaneCols


## 1.1.79 - 2023-Oct 18: - Command Divider and Title options
- update styles on new Divider and Title
- update sample to have each in it's own row
- add onClick to Title and Divider as well
- add Divider and Title to buildQuickCommands


## 1.1.78 - 2023-Oct 18: - Command Divider and Title options
-  https://github.com/mikezimm/drilldown7/issues/237
- create export type IQuickButtonType = 'label-only' | 'divider'; add to IQuickButton :  type?: IQuickButtonType;
- update SampleCommands.ts object to include both a divider AND label
- update createPanelButtonsV2 to create the divider and label object.

## 1.1.77 - 2023-Oct 18: - updateListItem
- update updateReactListItem to solve error when there is a proposed text update to a link column.
- update updateReactListItem get correct currentUrl.
- add way to show CommandButton Code in panel:
- add showCommandCode to IReactListItemsState
- update _panelButtonClickedv2 to accept event and if ctrlKey OR altKey is true, set showCommandCode to true
- update createPanelButtonsV2 to accept event and if true, show ReactJSON for each button below it's row.
- Add ctrl-click Tip to Commands help.

## 1.1.76 - 2023-Oct 18: - updateListItem
- update ListPerformance bold samples
- add link and spo types to SampleCommands:  "SharePointLink": "{{spo require}}", "OtherLink": "{{link require}}"
- update Commands.tsx PropPaneHelp to include examples for links
- update 'updateReactListItem.tsx' for new link logic.

## 1.1.75 - 2023-Oct 16: - Drilldown
- fix StringFunctions flex-wrap css and order

## 1.1.74 - 2023-Oct 16: - Drilldown
- fix StringFunctions flex arrays and ListPerformance link to Odata Operators

## 1.1.73 - 2023-Oct 16: - Drilldown functions
- bump to npm install @mikezimm/fps-pnp2@1.0.52 - for getTodayRestFilter
- update ListPerformance.tsx for example of rest filter using [Today]
- update getSelectColumns in /getVX/getSelectV2 to replace ???? due to new Drilldown function
- RECREATE IStateSourceNav  in getWebNav... apparently was hard coded in Drilldown but not carried back here.

## 1.1.72 - 2023-Oct 16: - Drilldown functions
- update createItemFunctionProp and IGetInterfaceV2.ts with new function options
- update RefinerRules.tsx for Date tips
- update StringFunctions.tsx to include new Number functions as well as adding more text help
- create function convertNumbers for Drilldown to process numbers to various scales.
- create new Date functions:  '????-MM-DD' and 'MM-DD'

## 1.1.72 - 2023-Oct 10: - Links and SourcePages - From HubConnections Navigation page
- add optional status?: number to IFPSItemLink, IFPSHubNavigationItem 
- add optional forceRender?: string; to ISourcePagesProps and SourcePages didUpdate  to force a complete rerender
- update _LinkStatus to return -1 if url is Navigation Header fake url

## 1.1.72 - 2023-Oct 10: - Update FPSItem, FPSTile to have true altClick as callback
- update FpsCompactTile to match new altClick on FPSTileElement

## 1.1.71 - 2023-Oct 14: - Update FPSItem, FPSTile to have true altClick as callback
- update IFPSItemLink:  change the 5 'clicks' to be like alt'Url' when you have hard coded url.
- update IFPSItemLink:  change altClick to be a true onClick type event
- update onFPSClick for IFPSItemLink changes
- update FPSTileElement to handle the new altClick
- update buildFPSAnyTileItems and buildFPSSubHubTileItems for new interface


## 1.1.70 - 2023-Oct 10: - Various Drilldown updates
- update ListPerformance.tsx to include instructions for filtering large lists  https://github.com/mikezimm/drilldown7/issues/318
- updated Icon import to be more specific:  FPSTextInput
- update Drilldown help:  SampleCommands - with working IconName value.
- update createPanelButtonsV2 to simplify button styles.

## 1.1.69 - 2023-Oct 10: - Various Drilldown updates
- update getCountLabel to be cleaner and also just return the number like '5' if the value did not have a decimal... like 5.00000 instead of 5.0
- update StringFunctions.WebPartHelpElement help info for Drilldown
- add new StringFunction:  TitleCase to >> ITrimWords, DoNotExpandTrimWords and createItemFunctionProp
- create new function:  get1stDigitFromString gets first digit from a string
- fix getLetterBuckets to work property by getting proper number from firstOrLast AND converting 'FirstInFirst5Buckets'.toLowerCase():  https://github.com/mikezimm/drilldown7/issues/361
- update PropPaneHelp/StringFunctions https://github.com/mikezimm/drilldown7/issues/361
- update createPanelAttachmentElements to add some padding at bottom:  https://github.com/mikezimm/drilldown7/issues/359


## 1.1.68 - 2023-Oct 08: - SourcePages MultiSelect updates
- update SourcePages _multiCall:  set this._retainViewXdidUpdates = 1; when select/un visible items, 0 when clear
- update SourcePages componentDidUpdate to add topSearch: [], where it was missing.
- update SourcePages componentDidUpdate stringify primarySource before testing for update.
- update SourcePages render:  Update rowCSS for topButtons so they look better.

## 1.1.67 - 2023-Oct 08: - SourcePages MultiCall udpates
- send sendThese back to parent: this.props.multiSelectCall( command, sendThese );
- update multiSelectButtonRowProps: to onClick: this._multiCall >>> this._multiCall.bind( this ),
- create sendThese[] and filter to send back correct items.  Was previously sending back all items
- update _multiCall to also check for  !this.props.onParentCallMultiClick || 

## 1.1.66 - 2023-Oct 08: - SourcePages onParentCallMultiClick - for Shift Clicking range of items
- add onParentCallMultiClick to ISourcePagesProps
- add lastItemMultiClickIdx to ISourcePagesState
- update ISourceRowRender:  onClick, onPropFilter, onTextFilter, onOpenPanel, onParentCall: event: React.MouseEvent
- update this._parentCall logic to test for shift click and call back correct function and item(s)


## 1.1.65 - 2023-Oct 06: - SourcePages multi-select buttons
- add farRightEle to ISourceSearchAgeHookProps as optional element
- update SourceSearchAgeHook for ageLement and farRightElement >> add ternary : undefined
- create IMultiSelectCommand and DefaultMultiSelectCommands
- create IFPSMultiSelectSourceProps for optional multi-select buttons
- extend ISourcePagesProps with IFPSMultiSelectSourceProps
- update ISourceButtonRowProps:  Icons?: string[]; // Added for future use
- update SourcePages:  add optional MultiSelectEle element if required to SearchBoxRowAge component


## 1.1.64 - 2023-Oct 05: - Various HubCon
- update analytics page handling of analyticsOptionsX.  Suggested web par class when not used:  // this._analyticsOptionsX = [];  https://github.com/fps-solutions/HubCon/issues/33
- update summarizeArrayByKey to skip resorting when key= 'createdAge' because created == Id and will always show latest Date and Id on top.  https://github.com/mikezimm/fps-library-v2/issues/120
- update itemProperties getValidPropLI to make link fields shorter so the icon does not wrap.  https://github.com/mikezimm/fps-library-v2/issues/122
- add retainViewXdidUpdates logic to onParentCall in ISourcePagesProps and ISourceRowRender https://github.com/fps-solutions/HubCon/issues/46
- update SourcePages componentDidUpdate to check for retainViewXdidUpdates and allow for not refiltering when selecting filtered or ageFiltered items.  https://github.com/fps-solutions/HubCon/issues/46


## 1.1.63 - 2023-Oct 05: - Various HubCon
- add departmentId to IFPSEnviro and FPSEnviro
- upgrade SourcePages to:  hide table portion if there is an error... Should show while loading or Success
- update doSpJsFetch to always prepend fetch https:// if the fetchAPI starts with tentant.sharepoint.com since it should always have that part.
- update IFPSBaseContentType  to include 'hub'

## 1.1.63 - 2023-Oct 05: - Various HubCon
- Change createUniversalIcons SPO Icons to be SPO Teal
- change STSWeb Icon from RowsChild to Org to match Compliance
- update IFPSNavType to include 'OnPrem' | 'Public' | '3rd Party'

## 1.1.62 - 2023-Oct 04: - ItemIsATeam ItemIsASite ItemIsAWeb
- Add to IItemIsAKeys:      'MSTeam'      | 'STSSite'     | 'STSWeb'      |
- Add to ItemIsAKeys:       'MSTeam'      , 'STSSite'     , 'STSWeb',
- Add to IItemIsAValues :   'ItemIsATeam' | 'ItemIsASite' | 'ItemIsAWeb'  |
- Add to ItemIsAValues:     ItemIsATeam    , ItemIsASite  ,  ItemIsAWeb,
- Add to createUniversalIcons:  Teams, Site and Web standard Icons
- Add standard iconNames:   MSTeam = 'TeamsLogo';   STSSite = 'SharepointLogo';   STSWeb = 'RowsChild';
- update processHubSubResults to accept adding IsAStuff[] to items

## 1.1.61 - 2023-Oct 02: - NA
- forgot to build...

## 1.1.60 - 2023-Oct 02: - update FPSTile Image/Icon logic
- fix FPSTilesWPHelp function name... forgot to update.
- update processHubSubResults to accept departmentId prop and sort so those sites are first
- keep sandbox function filterObjArrayByUniqueKeyLONGWAY based on filterObjArrayByUniqueKey which is preferred

## 1.1.59 - 2023-Oct 02: - update FPSTile Image/Icon logic
- updated IFPSFileImagePriority to include option for 'code' which is kind of like if the WP Prop was totally empty... but allows you to be specific if needed.
- updated choices in WP Props:  fpsTileFileImagePriorityChoices  to include:  { index: 1, key: 'code', text: "Predetermined Logic" },
- update FPSTiles >> getSrcAndIconBasedOnPriority so it properly uses the web part props setting first unless it's set to 'code'.
- Created FPSTilesWPHelp.tsx - for use with FPSTiles component in web part
- bump npm install @mikezimm/fps-styles@1.0.51 - GrayPropPaneAccordions.css
- added Readme for FPSTiles.md

- close HubCon #11 by updating FPSTileWPGroup with a label.

## 1.1.58 - 2023-Oct 02: - Modern Pages / FPSTextInput
- add padding to SingleModernPage
- migrate FPSTextInput from RTF-Fixer >> Hub Con improvements
- migrate formatJSONString, formatXml/formatHTML, isValidJSON, isXML/isHTML

## 1.1.57 - 2023-Sep 30: - Modern Pages
- update SingleModernPage to move the Prop Pain details and JSON behind the Toggle Details icon.
- add allHubs?: IAnySourceItem[];  to IStateSourceHubSubs // Added to filter down allHubs

## 1.1.57 - 2023-Sep 29: - Hub Nav
- correct logic in findSimilarNavNodes so it looks for .status instead of .ok becasue .ok is available on api calls return but not pnp
- correct logig in findSimilarNavNodes so that it looks for either nav.navigation ( from hub api ) or .items ( pnp web nav api )

## 1.1.56 - 2023-Sep 27: - Hub Nav
- update IFPSHubNav to have additional optional arrays:  itemsN and metaN
- add fpsCotnetType of 'nav' to result.fpsContentType in fetchMyHubNav
- migrate type IFPSNavType = 'Label' | 'Library' | 'List' | 'Page' | 'External' | 'Unknown' | 'TBD';
- add Props to IFPSHubNavigationItem :    selected: boolean;  NavPath: string[];  navType: IFPSNavType[];  FPSItem: IFPSItem;  FPSBreadCrumb: string[];
- add fpsContentType and index to getWebNav

## 1.1.55 - 2023-Sep 27: - Web Nav
- change INavErrorObj to be more consistant as IStateSourceNav

## 1.1.55 - 2023-Sep 26: - FPS Design Wizard
- update functions to allow FullBGImage on SPA Pages
    runFPSSuperOnInit, runFPSWebPartRender, addCanvasBGImageComponent, updateSectionBGStyles, getWebPartHelpElementCSSWarning 


## 1.1.54 - 2023-Sep 26: - FPS Design Wizard
- fix createLogic quotes issue:  // https://github.com/fps-solutions/FPS-Design-Wizard/issues/14
- update gitFPSDesignWizard style to small
- update bannerPillShape style in PropPaneColsClass.tsx

## 1.1.53 - 2023-Sep 26: - FPS Design Wizard
- update FieldPanel for new FPS Design Wizard web part... add bannerPillShape margin
- add gitFPSDesignWizard

## 1.1.52 - 2023-Sep 26: - Drilldown Issues - Fixes from updates
- updateReactListItem:  Update logic for Rich, Required, Append section

## 1.1.52 - 2023-Sep 25: - Drilldown Issues - Fixes from updates
- ADD NOTES for sourceButtonRow when props are undefined as in analyticsPage

## 1.1.51 - 2023-Sep 25: - Drilldown Issues - Fixes from updates
- update userComment... was showing <span></span> for some.  src\components\molecules\ReactListV1\functions\updateReactListItem.tsx
- update convertUTCTime to show a label when 'opposite' of label....
- update getBestTimeDelta - now AUTOMATICALLY adds 'ago' or 'from now' depending on what is needed.

## 1.1.50 - 2023-Sep 25: - Drilldown Issues
- Remove duplicate Audience related interfaces:  src\banner\propPane\Audiences\Interfaces.ts
- Reference these interfaces:  src\banner\propPane\Audiences\AudiencePropGroup.ts
- ReactListView updates
-   add to IReactListItemsProps: richMarginAuto, listNewForm, listViewForm, itemLinkSource, bannerProps
-   richMarginAuto: default = true, resolves Drilldown issue of classic rich text margin for some cases.
-   listNewForm:  custom NewItem form url
-   listViewForm:  custom ViewItem form url
-   itemLinkSource:  custom source paramter for when you close a form
-   updateReactListItem:  Fix cases when user presses Cancel when for Command button
-   createItemFunctionProp, ITrimWords:  Update to include options for 'ALLUPPERCASE' | 'alllowercase'
-   convertUTCTime , ITrimTimes:  Update to include options for 'DaysAgo' | 'WeeksAgo' | 'DaysFromNow' | 'WeeksFromNow' | 'TimeFromNow'
-   create ITimeDeltaInWhat for Time functions:  getTimeDelta, getAge
-   css class: fps-gen-goToLink-theme - Correct link color from theme

## 1.1.49 - 2023-Sep 20: - New repoLinks
- update IMyProgress due to missed updates from prior version.
       refLabel: string; step: string;  verb: string;  status: string;  checkValue: any;  returnField: any;  item: any;
- create new repoLinks for:  gitProvisionPal and gitRtfFixer

## 1.1.48 - 2023-Sep 20: - fps-pnp2
- bump npm install @mikezimm/fps-pnp2@1.0.51 - add AlreadyExisted to IFPSResultStatus  and FPSResultCommonErrors

## 1.1.47 - 2023-Sep 20: - RichText Editor
- update ISourceButtonRowProps: add disabled? prop for disabling buttons, add descEle? for small description text in block element below buttons
- migrate FPSTemplates.ts, IDefinedLists.ts, IMakeThisList.ts from FPS-Form Provsioning component
- update saveAssist function from EasyContents for reuse in Provisioning.
- update saveProvisioning function from EasyContents for reuse in Provisioning.

## 1.1.47 - 2023-Sep 18: - Various Provisioning Accordion
- Update IMyProgress to include:  timeMS, rowLabel, current, ofThese, array, id ( to combine setProgress and notify functions in Easy Contents logging )
- add contentStylesHidden to IMinAccordionProps to allow flexibility of having content partially visible when collapsed ( like a peak mode )
- add to IListInfo ( Provisioning ):  BaseTemplate?: number; Base?: number; DefaultViewPath?: any; DefaultViewUrl?: string;
- add to IViewField ( Provisioning ): 2023-09-15:  Added these to improve viewServices logic just adding it to the view definition itself.
      foundView?: boolean;  actualViewSchema?: string; viewFieldsSchemaString?: string; viewWhereXML?: string; viewOrderByXML?: string; viewGroupByXML?: string; errMess?: string;
- add to IZSentAnalytics ( Provisioning ): TargetList?: ISimpleLink; SiteLink?: ISimpleLink;
- refactor loadProperties logic in saveAnalytics2
- only update finalSaveObject.SiteLink in saveAnalytics2 if it does not exist... that way a custom one can be passed in.
- migrate saveAssist function from EasyContents for reuse in Provisioning.
- migrate saveProvisioning function from EasyContents for reuse in Provisioning.

## 1.1.47 - 2023-Sep 05: - Various Provisioning related
- add slash between webUrl and webRelativeLink in gotoListLink's onClick function
- add webPartFPSItem test in src\components\molecules\FPSTiles\functions\Any\createErrorFPSTileItem.tsx
- fix indexOf() > -1 in src/logic/Erros/friendly.ts

## 1.1.46 - 2023-Sep 03: - Update ListTemplate files
- create Provisioning function:  replaceTitleWithThisColumn
- create ootbLinkFilename 

## 1.1.45 - 2023-Sep 03: - Migrate ListTemplate files from npmFunctions
- create getXYearsAsNumbers and getXYearsAsStrings for building Year provisioning column
- migrate src\Lists_\XYZ to src\components\molecules\Provisioning
- migrate src\Lists_\colummTypes_.ts
- migrate src\Lists_\viewTypes_.ts
- migrate src\Lists_\listTypes_.ts
- migrate src\Lists_\columnsOOTB.ts

## 1.1.44 - 2023-Aug 18: - PageContextCopy_15_2_Site and IPerformance - Library Provisioning
- add serverRelativeUrl to PageContextCopy_15_2_Site
- add 'create' group to IPerformance --> IUnifiedPerformanceOpsKeys , IFpsErrorObjectOpKeys
- add create to ILoadPerformance { ops: create? }
- add create0 to create12 to ILoadPerformance { ops: create0? }
- add create to IMinPerformance { ops: create? }
- add create0 to create12 to IMinPerformance { ops: create0? }

## 1.1.43 - 2023-Aug 17: - FPS ListItemPicker
- update apiFetchFilesQuery to include select:  FileSystemObjectType
- update cleanWebFileList to exclude folders if there are no file type filters: FileSystemObjectType === 1
- update onListItemPropPaneStart to change wpProps.webUrlPickerValue if === 'CurrentSite'
- update testValidWebUrl to return true if the web is valid and approvedWebs is empty
- update src\banner\components\ItemPicker\README-ListItemPicker.md

## 1.1.41 - 2023-Aug 17: - FPS ListItemPicker
- Migrate ListItemPicker from SecureScript web part into src\banner\components\ItemPicker
- Add Interface/Init values to IThisFPSWebPartClass and FPSBaseClass
- add src\banner\components\ItemPicker\README-ListItemPicker.md

## 1.1.40 - 2023-Aug 15: - FPS Accordion
- add titleClass, componentClass to IMinAccordionProps
- change contentStyles to contentStylesVis in IMinAccordionProps
- change refreshId to IMinAccordionProps to force update if content has updated

## 1.1.40 - 2023-Aug 10: - PropPanelHelpMessage
- fix fps-pph-look-here relavent classes determined in src\banner\bannerX\FetchBannerX.tsx

## 1.1.39 - 2023-Aug 10: - Banner - PropPanelHelpMessage
- updated for new Help-Look bar:  npm install @mikezimm/fps-styles@1.0.47
- add HelpMessage to banner when PropPane Help is NOT visible but you are in Edit Mode.
- dynamically add classes to banner when appropriate:  'fps-display-edit' : 'fps-display-view', 'bannerPillShapeSideMargin'
- fix analyticsPage checkDeepProperty call
- updated checkDeepProperty to now handle when obj === null || undefined

## 1.1.37 - 2023-Aug 10: - SecureScript7V2 sourceButtonRow
- update:  ISourceButtonRowProps --> add optional rowCSS?: React.CSSProperties; buttonCSS?: React.CSSProperties;
- update createPerformanceRows to take minMSToShow
- count if rows with ms value > minMSToShow and only return a value if there is something to show.
- in EasyAnalyticsHook, only show process Table if it's greater than 10ms

## 1.1.36 - 2023-Aug 10: - SecureScript7V2 sourceButtonRow
- update ISourceButtonRowProps and sourceButtonRow to include heading?: JSX.Element; // Heading above row of buttons
- update EasyAnalyticsHook to pass in heading Element  in OptionRowProps and ButtonRowProps

## 1.1.35 - 2023-Aug 10: - SecureScript7V2 updates
- add analyticsWebX & analyticsOptionsX to IEasyAnalyticsProps, EasyAnalyticsHook,
- add to createAnalyticsSourceProps, getAnalyticsSummary, createAnalyticsSourceProps
- add to _analyticsWebX: string = AnalyticsWeb; _analyticsOptionsX: string = [''] 
      to FPSBaseClass, IThisFPSWebPartClass 

## 1.1.34 - 2023-Aug 09: - Build/Refactor the getFPSTileItems series:  Items, Webs, Lists
- fix item.File undefined error in getEasyIcon
- create const CommonSuppressKeys: IItemIsAKeys[] 
- update createItemHighlights to accept surpressIsAKeys to not build those highlights
- create re-usable:  addFPSViewHighlightElements to add View and Highlights Elements to FPSItem.Elements
- create generic functions:  buildFPSAnyTileItems which creates baseline item.FPSItem.Image/Icon/Link
- move createErrorFPSTileItem to own file for easy re-use
- create makeFPSSubHubTiles
- rebuild getFPSHubTiles to use makeFPSSubHubTiles
- create getFPSItemTiles and getFPSListTiles which use makeFPSItemTiles and makeFPSListTiles
- create makeFPSItemTiles and makeFPSListTiles based on FPSTile Component and PivotTiles code

## 1.1.33 - 2023-Aug 08: tileFileImagePriority - determine how to handle file images ( not including site pages )
- added tileFileImagePriority to: IFPSTileElementExtras and IFpsTileComponentWPProps
- added tileFileImagePriority to: PreConfigFpsTileCompProps and changesFpsTileComp
- created IFPSFileImagePriority, FPSFileImagePriorityValues
- added tileFileImagePriority to PropPaneGroup: FPSTileWPGroup
- create getSrcAndIconBasedOnPriority to resuse selection logic between components

## 1.1.33 - 2023-Aug 07: add SearchTypes to addSearchFileDataItemsV2 to get iconName and iconColor
- add pst to StdFileKeys and StdFileSearchTypes (outlook file)
- add SearchTypes to addSearchMetaAllV2, addSearchFileDataV2 & addSearchFileDataItemsV2
- update FPSItem.Search props in addSearchFileDataV2 - passes in Title,Desc, all Types if provided 

## 1.1.33 - 2023-Aug 06: addSearchFileDataV2, ModernSitePagesColumnsPivotTiles
- update check4MissingSelects logic
- fix some File logic in addSearchFileDataV2
- update ModernSitePagesColumnsPivotTiles to use other standard arrays if possible.

## 1.1.32 - 2023-Aug 06: getSourceItems
- forgot save ModernSitePagesColumns

## 1.1.31 - 2023-Aug 06: getSourceItems
- add DocIcon to IAnyFileItem
- create addSearchMetaAllV2, addSearchFileDataItemsV2 for implimenting all PivotTiles file search
- merge libraryColumns into ModernSitePagesColumns
- add remaining ModernSitePagesColumns to IAnyPageItem and IAnyNewsItem 

## 1.1.30 - 2023-Aug 06: getSourceItems
- fix getSourceItems result.fpsContentType when sourceProps.fpsContentType === undefined

## 1.1.30 - 2023-Aug 03: FpsCompactTile - improve Compact style
- fix farContent content and postion in FpsCompactTile
- "@mikezimm/fps-styles": "^1.0.45"

## 1.1.29 - 2023-Aug 03: FpsCompactTile - improve Compact style
- create filterObjArrayByUniqueKey
- attempt to improve styling of tiles:  processHubSubResults
- create WebSourceProps from HubSubSourceProps
- update fetchMyHubsites:  result.fpsContentType = [ depth ];
- update FpsCompactTile by creating var:  showAsSize to use in adjusting styling during certain instances

## 1.1.28 - 2023-Aug 03: FpsCompactTile & css
- npm install @mikezimm/fps-styles@1.0.44
- add optional farContent to FpsCompactTile and FpsTileComponent, fetchMyHubsites, getHubAssocSites
- add optional depth: 'site' | 'web' to getFPSHubTiles
- fix mergeDeep  to not do anything on skips... was still setting target=source if it matched.  NEED TO VERIFY on FUNCTIONS though
- update buildFpsTileWPProps to also set min width when using small or med... but does not seem to do anything.  So also added it directly in component.
- add minWidth capability to FpsTileComponent when using small or med compact tile

## 1.1.27 - 2023-Aug 02: FpsCompactTile & css
- bump to npm install @mikezimm/fps-styles@1.0.43

## 1.1.26 - 2023-Aug 03: FpsCompactTile & css
- add FpsCompactTile component from PFS-Tile-Component
- add tileLayout property to FpsTileComponent which will determine layout for items
- add tileLayout to IFPSTileElementExtras, changesFpsTileComp, PreConfigFpsTileCompProps and IFpsTileComponentWPProps
- add PropPaneProperty called FPSTileLayoutChoiceProperty which can be used for simple mode.
- add FPSTileWPGroup to FPSTileWPGroup 
- add IFPSCompactTileSize , IFPSTileLayout and FPSTileLayoutValues 

## 1.1.26 - 2023-Aug 02: FPSTileComponet & css
- fix 'null' as string description in buildFPSSubHubTileItems
- set content1 and content2 as undefined in buildFPSSubHubTileItems
- clean up unused imports

## 1.1.25 - 2023-July 31: FPSTileComponet & css
- update components\atoms\Highlights\createContentViewsRecent.tsx:
    require('@mikezimm/fps-styles/dist/pubDate.css');

## 1.1.24 - 2023-July 31: FPSTileComponet & css
- add componentDidUpdate and refreshId to FpsTileComponent
- fix SubHub Highlights icons... ItemIsAKeys was missing ArchiveContent, PopularLifeTime='blue' now

## 1.1.23 - 2023-July 31: FPSTileComponet & css
- update IAnyWeb  to add SiteLogo and PictureThumbnailURL due to different responses from different fetches
- update css require statements for FpsTileComponent
- update IFpsTileComponentProps  to include className & reactStyles, bannerProps added as well but not currently used.
- update buildFPSSubHubTileItems to get imageUrl from alternate results properties ( SiteLogoUrl, PictureThumbnailURL ) depending on api used
- update getFPSHubTiles to return IStateSourceHubSubs
- create HubSubSourceProps for use with Hub Con
- add SiteLogoUrl to hubSelects so it gets logos in more types of return objects

## 1.1.22 - 2023-July 31: FPSTileComponet & css
- create changesFpsTileComp and PreConfigFpsTileCompProps

## 1.1.21 - 2023-July 31: FPSTileComponet & css
- migrate actual FpsTileComponent
- update css require statements for FpsTileComponent

## 1.1.20 - 2023-July 31: FPSTileComponet css
npm install @mikezimm/fps-styles@1.0.41

## 1.1.19 - 2023-July 31: getFPSHubTiles, PivotTiles/FPSTileComponet migration
- create createErrorFPSTileItem in src\components\molecules\FPSTiles\functions\ErrorMessages.tsx
- update getFPSHubTiles to create error Tile in results if needed.


## 1.1.19 - 2023-July 30: getFPSHubTiles, PivotTiles/FPSTileComponet migration
- change addOtherIsAMeta to addListIsAMeta, remove from addSearchMeta1 << MUST BE ADDED WHERE LISTS ARE USED >>
- create getFPSHubTiles, processHubSubResults, buildFPSSubHubTileItems which was derived from 
-     PivotTiles:  getHubAssocSites and BuildTileCollection but does not add category props.
-     However, is baseline fetch for getting HubSites for FPSTiles
- migrate FPSTileWPGroup and x from FPSTileComponent
- create buildFpsTileWPProps to IFpsTileComponentWPProps  up WPProps
- refactor SpHttp\HubsSubs functions to ./fetches, ./functiuons and ./interfaces
- migrage createContentItemCount, createContentPubDate, createContentViewsRecent and createItemHighlights from PivotTiles

## 1.1.19 - 2023-July 30: addSearchMeta
- replace string ItemTypes in StdFileSearchTypes with const values
- add ContentGroupArchive, ItemIsArchiveContent to both IsA and also Search
- add "tar", "rar", "lzh" to StdFileKeys
- change addDateTimeFileInfoSearch to addDateTimeInfoSearch because I moved File things to it's own file.
- add createdNote and modifiedNote to IFPSItemStamp and addDateTimeFileInfoSearch
- create addSearchMetaAll which will do all the addSearch functions
- clean up the addSearchMeta functions

## 1.1.17/18 - 2023-July 27: IsA
- create addSearchFileData and refactor all IsAFile stuff from addSearchMeta1 and other places into addSearchFileData
- update addOtherIsAMeta to include looking for ItemIsCheckedOut

## 1.1.16 - 2023-July 27: IsA
- fix some interfaces for IsA based on FPS-Tile-Component Testing
-   make IsA required, IsA.allIsAKeys required, add IsA to FPSItem in both addDateTimeFileInfoSearch and createKeyObject

## 1.1.15 - 2023-July 27: IsA
- add PopularLifeTime, PopularRecent to IAnySearchableItem
- change ItemWasLifeTime to ItemWasPopularLifeTime
- migrate addPopularityToItems and markPopular :  guidance is to run addPopularityToItems AFTER addSearchMeta1

## 1.1.14 - 2023-July 27: IsA
- create IFPSBaseContentType which could be used for various improvements like only doing certain addItemIsA functions
- add fpsContentType to ISourceProps and IStateSource
- add fpsContentType[] to all Empty objects of ISourceProps and IStateSource
- add fpsContentType[] to checkItemsResults and checkAnyResults
- update fpsContentType array in all the existing 'get' functions after doing checkItemsResults and checkAnyResults
- create IFPSHighlights interface for the Highlight Elements
- create UniversalIconsPT:IFPSHighlights object with all Highlight Elements
- create IAnySearchableItem  and add it to IAnySourceItem
- create getIsAListHighlights, getIsAListHighlightsPT and getIsAWebHighlightsPT
- change IconName for ForceCheckout to RequiresCheckout.  ForceCheckout is the prop on the library.  But RequiresCheckout tells the story better in the code.

## 1.1.13 - 2023-July 25: IAnyItem, IsA, FPSTile improvements
- break IAnySourceItem into extended interfaces like IAnyWeb, IAnyListLib and IAnySecurableItem to make it easier to re-use interfaces in more focused fashion
- import some more IsA props and logic from PivotTiles
- refactor IsA and IAnyItem to have more focused building blocks
- update addDateTimeFileInfoSearch to add props into item.File for items that only have ServerRelativeUrl
- add altClick, ctrlClick, shiftClick, metaClick, key3Click to IFPSItemLink for future component usage
- create IFPSItemElements for passing into FPSItem for Tile component - into IAnySourceItem 

## 1.1.12 - 2023-July 20: EA improvements
- move getPageTitle to it's own file for easier re-use
- rebuild buildAnalyticsSummary to not update searchTextLC every step of the way.  Just do it at the end
- add PageTitle to item.FPSItem.Search.searchText;
- update summarizeArrayByKey to fix searchText and also some mapping.

## 1.1.11 - 2023-July 20: EA improvements
- create addDeepPropsToSearch function which is used for adding searchText to analytics items
- create getDeepValuesStringArray function which can get an array of strings based on an array of deepPropKeys and an item.
- create getDeepValuesArray which is the same as getDeepValuesStringArray except does not convert to a string.
- add getHighlightedText for EA optionalColumns1 and optionalColumns2 columns

## 1.1.10 - 2023-July 20: EA improvements
- fix analyticsPage.tsx useState function
- add wpFilterProps to getAnalyticsSummary 
- add FPSItem: IFPSItem; IOjbectKeySummaryItem so Bar summaries can be searched
- create function getSumableNumber which converts all types to a number you can do like:  x += getSumableNumber(y)

## 1.1.9 - 2023-July 20: EA improvements
- add Fetch-Avg ms to FilterButton EA RowBar.tsx
- add to buildAnalyticsSummary:  item.FPSPropsObj = JSON.parse( item.FPSProps );
- fix summarizeArrayByKey logic
- add FPSPropsObj?: any; to IZFetchedAnalytics for use in EA

## 1.1.8 - 2023-July 19: EA improvements
- add optionalColumns1, optionalColumns2 to ISourcePagesProps
- add optionalColumns1, optionalColumns2 to SourcePages.renderRow build up
- update analyticsPage to get updated EzSummary: IAnalyticsSummary, useThisState, pass in optionalColumns1/2 into SourcePages
- fix Row.tsx props.optionalColumns1/2.map to have correct return statement
- expand IOjbectKeySummaryItem to have placeholder keys of x0, x1, x2, x3 to accomodate up to 4 filter buttons from web part

## 1.1.7 - 2023-July 19: EA improvements
- add _wpTDLeft, _wpTDRight and _wpFilterProps to IThisFPSWebPartClass, add to easyAnalyticsProps in mainWebPartRenderBannerSetupX

## 1.1.6 - 2023-July 19: EA improvements
- add optionalColumns1, optionalColumns2 to ISourceRowRender to be able to pass into row render functions and add extra columns
- create getDeepestSplits function for helping getting Property Keys for headings and filter buttons.
- add wpTDLeft, wpTDRight IEasyAnalyticsProps for extra columns per web part - #78
- add wpFilterProps to IEasyAnalyticsProps for specific filters per web part - #79
- add customElement1B, customElement1C, customElement2B and customElement3 to IItemPaneProps and ICustomPanel
- add PFSProps to EasyAnalytics Panel
- update buildAnalyticsSummary to update item's searchText and searchTextLC correctly
- update EasyAnalytics to have onClick for Id and perf with -na- value

## 1.1.5 - 2023-July 19: Fix AgeSlider filter in SourcePages & Search
- put back createdAge, modifiedAge on IAnyContent AND publishedAge to IAnyNewsItem for easier search in AgeSlider
- fix addSearchMeta to add StampAge to main item so it can be used in existing AgeSlider code
- fix null error in EasyPages\Analytics\components\Row.tsx for item.FPSInfo.Stamp.created.age

## 1.1.4 - 2023-July 18: Fix blanket office-ui-fabric-react imports
- fix office-ui-fabric-react import in src\components\atoms\Links\CreateLinks.tsx - was blanket import
- fix office-ui-fabric-react import in src\common\PropPaneHelp\preconfig\SitePresetsInfo.tsx - was blanket import

## 1.1.3 - 2023-July 8: Fix some EasyIcons issues
- work on EasyPages duplicate Tabs issue
- create NoDups version of string functions:  getStringArrayFromStringNoDups, getNumberArrayFromStringNoDups
- update createEasyPagesExtraWPProps, createEasyIconsWPProps to use getStringArrayFromStringNoDups
- update getUsedTabs to NOT return duplicates from array

## 1.1.2 - 2023-July 6: Fix some EasyIcons issues
- add to 'FileTypes' to EasyIconDefaultKeys
- change FileTypes 'Folder from 'Words' to 'FileTypes'

## 1.1.1 - 2023-July 6: Fix some EasyIcons issues
- revise getPagesContent to get items = addSearchMeta1( items, sourceProps, null ); before addEasyIcons
- revise addEasyIcons to first use getEasySystemIcon for Non List/Lib Icons, then later do those after all others have been exhausted
- revise addSearchMeta1 to create base FPSItem object on items right away.

## 1.1.0 - 2023-July 6: BREAKING Refactoring IAnySourceItem by moving to IFPSItem sub object
- Moved to IAnyContent to new folder src\components\molecules\AnyContent
- Moved to IFPSFileObject src\components\molecules\AnyContent\IFPSFileObject.ts
- Restructured all existing IAnySourceItem properties and interfaces that this library adds to the default IAnySourceItem to the sub object:
      export interface IAnySourceItem extends IAnyListItem, IAnyFileItem, IAnyPageItem, IAnyNewsItem, IAnySecurableItem  {
        FPSItem: IFPSItem;
      }
- Moved OOTB common SharePoint properties into IAnyListItem, IAnyFileItem, IAnyPageItem, IAnyNewsItem, IAnySecurableItem
    so they can be extended or used in more focused manner when applicable.
- Made IAnySourceItem NOT include Partial<Any> in order to have more strict typing.
- Created additional interface for use ONLY where IAnySourceItem needs to be cast as any
    export interface IAnySourceItemAny extends IAnySourceItem, Partial<any>  { }
- rebuilds all functions that manipulate or use those properties to use the tree structure
- All web parts that upgrade from 1.0.256 to 1.1.0 need to go through additional testing including:
    related functions and components


## 1.0.256 - 2023-June-30: anlyticsRow, repoLinks
- add cursor: pointer to analytics perf cell,
- update fps repoLinks style to Legacy, fix CorePFS1173+ links to use fps-solutions github

## 1.0.255 - 2023-June-30: analyticsPage
- fix row onParentCall

## 1.0.254 - 2023-June-30: analyticsPage onParentCall
- fix analyticsPage onParentCall not working on pareto bar charts

## 1.0.253 - 2023-June-30: repoLinks, fetch order, logging constants
- BREAKING:  break apart repo links into individual files to improve imports src\components\atoms\Links\RepoLinks\LinksRepos.tsx
- bump fps-pnpv2 to 1.0.50 to fix orderBy on fetch to properly sort ascending - easyAnalytics
- split logging/constants.ts into separate files in Interfaces folder:  common, EasyContents, ExtremeStorage, analytics

## 1.0.252 - 2023-June-30: office-ui-fabric-react
- clean up office-ui-fabric-react imports -- refer imports to lib folders

## 1.0.251 - 2023-June-27: EasyIcons stuff
- add Email to Nouns eiTypes  https://github.com/mikezimm/fps-library-v2/issues/72
- add File?: IFpsFileProperty;  to IMinStandardIconObject 
- add Zip file compatibility to getEasyIcon  https://github.com/mikezimm/fps-library-v2/issues/70
- move IFpsFileProperty to it's own file for smaller importing

## 1.0.250 - 2023-June-27: easyAnalytics.css, _wpInfoGroupExpanded
- fix WebPartInfoGroup expanded logic with_wpInfoGroupExpanded

## 1.0.249 - 2023-June-27: easyAnalytics.css, _wpInfoGroupExpanded
- add _wpInfoGroupExpanded to IThisFPSWebPartClass, FPSBaseClass and WebPartInfoGroup
- use _wpInfoGroupExpanded to set expanded property of WebPartInfoGroup
- npm install @mikezimm/fps-styles@1.0.40

## 1.0.248 - 2023-June-27: EasyAnalytics improvements
- add createPerformanceTableVisitor table in ItemPane
- update performance cell label
- change panel size to medium

## 1.0.247 - 2023-June-27: EasyAnalytics improvements
- fix page & gulp link urls.  Add page title  https://github.com/mikezimm/fps-library-v2/issues/73
- add performance ms and clickable panel to see performance object
- fix getBestAnalyticsLinkAndIcon to return best link
- add clickable performance label to show full performance JSON object in panel https://github.com/mikezimm/fps-library-v2/issues/74


## 1.0.246 - 2023-June-25: _allowPropsEasyMode
- Basic Logic: _allowPropsEasyMode is false by default and must be opted-in in web part onInit class.
-   If _allowPropsEasyMode === true && properties.propsEasyMode === true then some props and groups are hidden in the prop pane
-   If easyMode is allowed or enabled, WebPartInfo group is auto-expanded.  It has the toggle but it can also be added to a web part group.
- add propsEasyMode in IThisFPSWebPartClass, FPSBaseClass
- add propsEasyMode to importBlockPropsFPS
- add propsEasyMode in IMinBannerUtilityProps
- add propsEasyMode if it is set in the onInit via _allowPropsEasyMode
- set propsEasyMode: false, in PresetFPSBanner
- hide some groups in getAllDefaultFPSFeatureGroups if propsEasyMode !== false
- hide some props in FPSBanner4BasicGroup if propsEasyMode !== false

## 1.0.246 - 2023-June-25: doSpJsFetch, EasyIcons
- add to hubSelects:  'Created', 'Modified', 'LastItemUserModifiedDate'
- update logic in fetchMySubsites to get subs modified date per:  https://github.com/mikezimm/pivottiles7/issues/289
- add FAQ to Acronyms on EasyIcons
- update logic in src\components\molecules\SpHttp\doSpJsFetch.ts to resolve https://github.com/mikezimm/pivottiles7/issues/292
  checking for when there are no results because there are none to find.
  defined interfaces for search results object
  added rawSearchResults and fetchAPI to IJSFetchReturn
- created search api results interfaces:  IFPSSearchAPIResultsData, IFPSSecondaryQueryResults, IFPSSpecialTermResults,

## 1.0.245 - 2023-June-25:
- Just republishing. got strange error when using 1.0.244

## 1.0.245 - 2023-June-24: checkItemsResults, fetchMyHubNav
- update PresetFPSBanner >> bannerPillShape : true,
- add iconNames:  NoRecentViews, PopularRecent , PopularLifeTime
- add in standardPivotTiles.tsx:  NoRecentViews, PopularRecent, PopularLifeTime
- Move : statusNo?: number; statusText?: string; FROM: IJSFetchReturn TO IBlankErrorObj to better match doSpJsFetch return
- update cleanSearchedWebs to set thisItem.ServerRelativeUrl first if it does not exist
- add check4This in getFullUrlFromSlashSitesUrl vs showConsole << for cases where url is analytics >>
- update checkItemsResults to check for case where !e but there is an error.status = 'Error' ... getting e.statusNo = 500 now
- deprecate getAssocSites since now using diret fetch api

## 1.0.243 - 2023-June-24: checkItemsResults, fetchMyHubNav
- update checkItemsResults to include trace string in console message
- update fetchMyHubNav to get the count of nav links for performance including all children

## 1.0.242 - 2023-June-23: Refactor SpHttp fetches, add Nav calls
- standardize all SpHttp/HubsSub to first add unifiedPerformanceEnd then do checkItemsResults
    fetchMyHubNav, fetchMyHubsites, fetchMySubsites
- create addWebNav, getWebNav as wrapper for pnpv2 calls
- replace some double quotes on imports of new functions


## 1.0.241 - 2023-June-23: Migrate SpHttp/HubsSub from HubCon, add unifiedPerformanceEnd
- created unifiedPerformanceEnd in Performance/functions to help with the new unifiedPerformanceOps
- created types:  IUnifiedPerformanceOpsKeys, IFpsErrorObjectOpKeys
- created doSpJsFetch & IJSFetchReturn
- created fetch to SP APIs:  fetchMyHubNav: IFPSHubNav , fetchMyHubsites, fetchMySubsites: IJSFetchReturn
- created fetchMyHubSubs: IFPSHubsSubs
- created logic to clean up Hubs and Subs results:  cleanSearchedWebs
- created logic to find Nav Nodes:  findSimilarNavNodes, findSpecificNavNodes
- created SP Docs api interfaces:  IHubSiteDataResultAPI, IFPSHubNavigationItem
- created interfaces: IFPSWebsWithLogo, IFPSHubSiteDataDocsApi, IFPSHubSitesApi, IFPSHubSiteApi
- created interfaces: IFPSSubsFilteredItem and IFPSSubsSearchCleanItem

## 1.0.240 - 2023-June-18: Add new repos
- add baseFPSRepos
- add gitRepoHubConnections, gitRepoSpHttpTester

## 1.0.239 - 2023-June-14: Add Chinese OEMs to EasyIcons list
- update getEasyIcon to include recognize EasyIcons.Ignores: https://github.com/mikezimm/pivottiles7/issues/281
- change PerformanceTable row column order: Move Mode and MS to left one cell each  https://github.com/mikezimm/fps-library-v2/issues/57
- revise perforanceTable.startStr to have ... instead of : makes it easier to read

## 1.0.238 - 2023-June-14: Add Chinese OEMs to EasyIcons list
- Added CustomersCN, also added Volvo to general Customers list
- https://github.com/mikezimm/pivottiles7/issues/262 / https://github.com/mikezimm/fps-library-v2/issues/60
- Add SharePoint's system Icons to EasyIcons object so it should now be visible in prop pane help
- Note that SharePoint icons are added directly to the item via addEasyIcons >> getEasySystemIcon and is therefore skipped in getEasyIcon
- https://github.com/mikezimm/fps-library-v2/issues/67
- added Words and Keywords:  Archive, Archives, Templates, Forecast, Cost, Meeting
- added Acronyms: KPI, PSC, FMEA, DFMEA
- Gracefully support if imageUrl is OOTB like:  https://github.com/mikezimm/fps-library-v2/issues/59, https://github.com/mikezimm/pivottiles7/issues/261 & 280
- moved replaceDefaultIcons << DEPRECATED >> into it's own file because I baked the functionality into addEasyIcons now.

## 1.0.237 - 2023-June-13: Fixes based on testing:  itemsY to IStateSource
- add  unifiedPerformanceOps: {} to results: IFpsHttpInfo in createFPSHttpResponse
- add  unifiedPerformanceOps: {} to anyInput: IFpsErrorObject in checkAnyResults 
- add  unifiedPerformanceOps: {} to itemsInput: IFpsItemsReturn in checkItemsResults 
- add optional itemsY to IStateSource for cases when you need to be able to reset the items typing

## 1.0.236 - 2023-June-13: <<< BREAKING >>> - refactor all performanceOp in IFpsErrorObject
- <<< BREAKING >>>:  rename all performanceOp in IFpsErrorObject
- added Optional check...checks12 to IPerformance.ops
- removed: performanceOp: IPerformanceOp
- added:  fetchOp, checkOp, analyzeOp, processOp, renderOp, saveOp, unifiedPerformanceOps
- added:  unifiedPerformanceOps: IUnifiedPerformanceOps 
- COMMENTS:
    Logic is to build in more flexibility to have both fetch and other performance right in a single IFpsErrorObject.
    This reduces redunant performance objects in web part and component states... Single IStateSource has it all
    Also added unifiedPerformanceOps at the same time which is a single object with all the relavant performance for a Results object.
    The point of this is to start moving towards a single Performance object that contains multiple performances built in
- updated functions to add unifiedPerformanceOps:
  easyAnalyticsSummary, fetchAPI, getSourceList, getWebLists, getSourceItems, getFilteredSubSites, getSubSites, getWebInfoIncludingUniqueMin, getWebInfoIncludingUniqueAll


## 1.0.235 - 2023-June-13: - GetInterfaceV2, getSelectV2, getResizedImage
- added:  IDoNotFetchCalculated  and DoNotFetchCalculated - started with DocThumb and DocThumbnail for Pivot Tiles
- added:  DoNotFetchCalculated to DoNotExpandFuncColumns as well so they are checked.
- created: getResizedImage in src\logic\Links\GetResizedImageLink.ts ( from PivotTiles ) using @microsoft/sp-image-helper

## 1.0.234 - 2023-June-07: SinglePage
- fix !cell error when using heading column
- make heading tricks bold to highlight, also add some padding Top

## 1.0.233 - 2023-June-07: various Pivot Tiles
- update BannerHelpTricks to include { param: `fpsReactRender`, value: `true` , description: `log various during a React Component Render` }
- update 'Advanced' Pivot Tab in FullPanel.tsx from word `Advanced` to flicon:  `FilterSettings`
- update createTricksTable to allow for 'heading' of tricks, add to prebuilt ones.  https://github.com/mikezimm/pivottiles7/issues/269

## 1.0.232 - 2023-June-07: fps-styles@1.0.39
- @mikezimm/fps-styles@1.0.39

## 1.0.231 - 2023-June-03: console.log, SourcePages
- fix dcryptme code
- add check4This in some forceWebPartWhiteText and SectionStyles.ts
- fix SourcePages no items element to not be in single table cell wide
- change pph Pivot Tabs on CSSPerformance and CSSWarning to add icon

## 1.0.230 - 2023-June-03: propPaneHelp tabs
- npm install @mikezimm/fps-styles@1.0.38

## 1.0.229 - 2023-June-03: propPaneHelp tabs
- change Pivot Text from 'FPS Expand' to itemIcon='ChromeFullScree'
- change Pivot Text from 'Import' to itemIcon='Export'
- change Pivot Text from 'Visitor Help' to itemIcon='Unknown'
- change Pivot Text from 'Background' to itemIcon='PictureFill'

## 1.0.228 - 2023-June-02: _fpsSiteThemes,
- add siteThemes: ISiteThemes directly into IWebpartBannerProps 
- allow passing in optional siteThemes in FetchBannerX, no longer needed to pass in React Component

## 1.0.227 - 2023-June-02: _fpsSiteThemes,
- update protected _fpsSiteThemes: IFPSSiteThemes = null;

## 1.0.225 - 2023-June-02: _fpsSiteThemes, Age updates
- fix double 'ago' in AgeSliderOptions 
- tweak styling in src\components\atoms\FPSAgeSlider\FPSAgeHook.tsx
- update _fpsSiteThemes to:  MainClass,
- have runSuperOnInit spread out the individual classes to _fpsSiteThemeDark, _fpsSiteThemeLight, _fpsSiteThemePrimary

## 1.0.224 - 2023-June-02: showTricks and related
- tweak PageArrows padding and margin to be a little narrower
- create dcrptMe, fix check4Tricks logic
- FPSAgeHook - change style width work better with SourcePages
- SourceSearchHook - change style width work better with SourcePages
- update getFPSUser to use check4Tricks instead of local code which was the same.

## 1.0.223 - 2023-June-02: showTricks / bannerPillShape
- npm install @mikezimm/fps-styles@1.0.36

## 1.0.222 - 2023-June-02: showTricks / bannerPillShape
- move bannerPillShape class to 'easy-pages' parent component so it evenly applies to all sub pages.
- fix casing while checking.... have to lc the current credentials before comparing
- fix FetchPanel logic to make visible
- fix trickyEmails to be encrypted so it works correctly.

## 1.0.221 - 2023-June-01: easyAnalytics and SourcePages
- add new Class css classes to FPSBaseClass
- fix require('') in sourcePages to pull from fps-styles

## 1.0.220 - 2023-June-01: easyAnalytics and SourcePages
- add easyAnalyticsProps to IWebpartBannerProps using mainWebPartRenderBannerSetupX
- add to easyAnalytics to EasyPages and banner component
- update trickyCheck
- add _fpsSiteThemeDark, _fpsSiteThemeLight, _fpsSiteThemePrimary to:  MainClass
- pass themes into IWebpartBannerProps using mainWebPartRenderBannerSetupX

## 1.0.219 - 2023-June-01: easyAnalytics and SourcePages
- import EasyAnalytics and SourcePages from CoreFPS1152 and update all references
- create CommonUITricks in makeTricksTable
- add check4This before console.log in more functions.

## 1.0.218 - 2023-May-31: various
- commonize some css classes into CommonClasses
- commonize FPSFetchError, FPSFetchSpinner, FPSFetchStatus

## 1.0.217 - 2023-May-31: GetGoToWebLink
- add altWebText to GetGoToWebLink

## 1.0.216 - 2023-May-31: GetGoToWebLink
- create GetGoToWebLink

## 1.0.215 - 2023-May-31: getGoToLinks
- add optional item and list link css to getGoToLinks, GetGoToListLink, GetGoToItemLink

## 1.0.214 - 2023-May-31: getGoToLinks
- add gitRepoCoreFPS1152Small
- refactored getGoToLinks:  Now also split out  GetGoToListLink, getGoToItemLinkUrl & GetGoToItemLink


## 1.0.213 - 2023-May-31: EasyAnalytics
- fps-styles@1.0.33 - add white-space: pre-wrap to .list-view-rt in reactListView.css (Drilldown)
- fix buildAnalyticsSummary( lower case things )

## 1.0.212 - 2023-May-31: EasyAnalytics
- create SearchBoxRowAge.tsx:  https://github.com/mikezimm/fps-library-v2/issues/64
- remove paddingLeft: 30px from pageArrowStyles

## 1.0.211 - 2023-May-28: EasyAnalytics
- add Id and CodeVersion to createAnalyticsSourceProps
- add createdD, modifiedD, publishedD to IAnySourceItem, ISavePropsItem and addDateTimeFileInfoSearch which has the simple sortable zulu date stamp
- add padding to createPerformanceRows cells
- update getFilteredItems to prevent error https://github.com/mikezimm/fps-library-v2/issues/62
- add analyticsPage interfacesIOjbectKeySummaryItem , IObjArraySummary, IAnalyticsSummary , 
- add analyticsPage functions: reateKeyObject, easyAnalyticsSummary, summarizeArrayByKey, getDateLabel
- add additional arrays to IStateSourceA :  itemsS, itemsO, itemsP

## 1.0.210 - 2023-May-28: EasyAnalytics
- fix webRelativeLink in AnalyticsSourceProps
- fix buildAnalyticsSummary:  meta1 and meta2

## 1.0.209 - 2023-May-28: EasyAnalytics
- add prepSourceColumns to createAnalyticsSourceProps
- add IZFetchedAnalytics to IStateSourceA
- create retrieveFPSEnviro
- create addGulpParam and removeGulpParam in src\components\atoms\Links\GulpLinks.ts
- extend IStateSource and EmptyStateSource with itemsA, items1, items2, meta1, meta2
- update buildAnalyticsSummary:  add addSearchMeta1, look for Mine, Others, ThisSite, OtherSite and add to meta1

## 1.0.208 - 2023-May-28: EasyAnalytics
- separate createAnalyticsSourceProps, buildAnalyticsSummary << just framework for future use
- create IStateSourceA , simplify getAnalyticsSummary

## 1.0.207 - 2023-May-28: EasyAnalytics
- reorganize EasyPages folder and update all references

## 1.0.206 - 2023-May-28: EasyAnalytics
- fix Images EasyIcon iamge Url
- add trickyAnalytics group
- restructre EasyPages into folders and functional files
- functions:  compoundArrayFilter
- analyticsListX to IWebpartBannerProps, IMinBannerUtilityProps, mainWebPartRenderBannerSetupX, createEasyPagesExtraWPProps
- _analyticsListX to FPSBaseClass, IThisFPSWebPartClass
- update check4Tricks for when user === null - will use FPSUser instead
- break out: IEasyPagesPageProps, IEasyPagesSourceProps 
- begin adding functionality for EasyAnalytics in componentSources and componentPage
- add TrickyMMc 

## 1.0.205 - 2023-May-26: Restructured atoms/EasyIcons, added EasySystemIcons
- add merge appendTitle into bannerProps for mainBannerContent
- update EasySystemLibraryIcons and EasySystemListIcons


## 1.0.204 - 2023-May-26: Restructured atoms/EasyIcons, added EasySystemIcons
- rename file:  src/components/atoms/EasyIcons/SystemIcons/ListTitlesWithNoSpaceUrls.ts to src/components/atoms/EasyIcons/SystemIcons/EasySystemLibraryIcons.ts 

## 1.0.203 - 2023-May-26: Restructured atoms/EasyIcons, added EasySystemIcons
- moved code into 3 folders:  interfaces, functions, SystemIcons
- broke apart some constants and interfaces into smaller files and moved to interfaces folder
- created IMinStandardIconObject for the Item object getting passed into some functions
- created 3 ISystemEasyIcon arrays:  AllEasySystemIcons, EasyCCSPageIcons, EasySystemListIcons, EasySystemLibraryIcons
- create getEasySystemIcon which will check typical object for a systemIcon

## 1.0.202 - 2023-May-26: EasyIcons
- create replaceDefaultIcons which looks for some SharePoint Icons and replaces if it can find a new one
- for https://github.com/mikezimm/fps-library-v2/issues/59 and https://github.com/mikezimm/pivottiles7/issues/261

## 1.0.201 - 2023-May-26: EasyIcons
- add Acronyms: IEasyIconGroup; AcronymsW: IEasyIconGroup;
- add optional paramter: 'defaultIcon' to getEasyIcon

## 1.0.200 - 2023-May-21: fps-styles@1.0.30
- update CSS Warning for fps-styles@1.0.29/30 updates

## 1.0.199 - 2023-May-21: fps-styles@1.0.30
npm install @mikezimm/fps-styles@1.0.30

## 1.0.198 - 2023-May-21: fps-styles@1.0.29
npm install @mikezimm/fps-styles@1.0.29

## 1.0.197 - 2023-May-19: startPerformOp
- @mikezimm/fps-styles@1.0.28
- Add PropPane Warning for:  src/components/molecules/FullPageBackGround/PropHelp/CSSWarning.tsx

## 1.0.196 - 2023-May-19: startPerformOp
- change _refreshBGStyles performance from BGStyles to BGStylesRefresh

## 1.0.195 - 2023-May-19: startPerformOp
- add MS to all startPerformOp as standard going forward:  https://github.com/mikezimm/Slick-Sections/issues/69

## 1.0.194 - 2023-May-19: fps-styles update
- npm install @mikezimm/fps-styles@1.0.27 ( for Hero forceWhiteText.css )

## 1.0.193 - 2023-May-19: beakerBannerElement & Icon from SlickSections 
- add _refreshBGStyles to IThisFPSWebPartClass & FPSBaseClass
- add enableTabs: boolean; to IFPSPageBGWPProps ( so SlickSections can pass it in to use in ShowParmaLinks in BeakerBannerElement )
- add beakerBannerContent?: JSX.Element; to IFetchBannerXProps 
- migrate code into updateFarElementsWhiteRefresh >> creates the RefreshWhite icon and also showBeakerBanner icon button
- build updateFarElementsWhiteRefresh() into farBannerElementsArray in FetchBannerX
- add ShowParmaLinks from SlickSections
- create BeakerBannerElement which has standardized ShowParmaLinks and beakerBannerContent


## 1.0.192 - 2023-May-19: FullBackground updates
- rename updateSectionStyles  to updateSectionBGStyles so that it was different than the 'other' updateSectionStyles which updates section widths.
- add _allowFullPageBG: IFullBackgroundMode; to IFPSPageBGWPProps in IWebpartBannerProps {fpsPageBGWPProps: }
- add _allowFullPageBG: IFullBasetup.main._allowFullPageBG,   into to bannerProps in BuildBannerPropsX2.ts
- add updateSectionBGStyles to main runFPSSuperOnInit
- add updateSectionBGStyles to main runFPSWebPartRender
- add to DefaultPivots:  getWebPartHelpElementCSSWarning, getWebPartHelpElementCSSPerformance, getFullBackgroundHelp


## 1.0.191 - 2023-May-19: Styles and FullBackground updates
- add updateSectionCSS.ts and SectionStyles.ts from SlickSections web part
- add defaultWPBack to FPSSlickBackgroundGroup
- add Background Color info to FullImage WebPartHelp
- add defaultWPBack to IFPSPageBGWPProps (duplicate of Common props from SlickSections)


## 1.0.190 - 2023-May-17: src/FPSPinMe.css
add overflow-y: scroll; to pinMeOverRideMxHt100P and pinMeOverRideMxHt560

## 1.0.189 - 2023-May-15: FPSMinMeOverRide
- updated FetchBannerX:  added to PinMe click:  this._heightOverRide( newSetting, this.state.showSettings ); for PageInfo issue

## 1.0.188 - 2023-May-15: RelatedItems and FPSMinMeOverRide
- updated RelatedItems errorInfo error
- fix RelatedItems/GetItems.ts fetch... added restFilter so items are actually filtered
- created FPSMinMeOverRide to address https://github.com/mikezimm/PageInfo/issues/125
- updated FPSPinMe.css in fps-styles
- updated FetchBannerX:  this._heightOverRide( newSetting, this.state.showSettings ); for PageInfo issue


## 1.0.187 - 2023-May-15: add getListByField, update fetchFpsItemAsSpecial, 
- add getListByField to get the props of a single field from list
- update fetchFpsPageAsSpecial:  require DoNotExpandThese

## 1.0.186 - 2023-May-15: add fetchFpsItemAsSpecial
- add fetchFpsItemAsSpecial to replace fetchFpsItemAsXML
- add fetchFpsPageAsSpecial to replace fetchFpsPageAsXML
- add Deprecate comments to fetchFpsItemAsXML, fetchFpsPageAsXML

## 1.0.185 - 2023-May-14: add getWebPartHelpElementRelatedProps
- add getWebPartHelpElementRelatedProps in src/components/molecules/RelatedItems/RelatedPropsHelp.tsx

## 1.0.184 - 2023-May-14: add _doHeadingStyles
- add _doHeadingStyles to class Interface
- add _doHeadingStyles default = false to main class


## 1.0.183 - 2023-May-14: migrated RelatedItems component in components/molecules
- migrated AND refactored GetItems to use getSourceItems in src/components/molecules/RelatedItems/RelatedItems.tsx
    now using IStateSource model
- migrated AND refactored IAnyContentRelated ( extendes IAnySourceItem ) in src/components/molecules/RelatedItems/RelatedState.ts
- migrated RelatedItemsPropGroup.ts to  src/components/molecules/RelatedItems/RelatedItemsPropGroup

## 1.0.183 - 2023-May-14: FPSPageInfo updates
- update FetchBannerX for forcing pinMeState via url:  // https://github.com/mikezimm/PageInfo/issues/116
- add 'transparentTdBorder' | 'lightTdBorder' | 'lightDashedTdBorder' to IFPSHeadingClass AND FPSMiscClasses  // https://github.com/mikezimm/PageInfo/issues/117
- add tabelTdStyle: string; to IMinHeadingStyleProps 
- add td?: IRegExTag; to IHTMLRegEx 
- add 'td' to IHTMLRegExKeys 
- add td: createTagRegex( 'td', 'Finds Table Cells in SharePoint Pages'), to HTMLRegEx
- create functions:  runStyleOnTags and getClassStyles, simplify applyHeadingCSS in src/logic/DOM/Headings/functions.ts

## 1.0.183 - 2023-May-11: clean up logging with check4This
- add PresetsTricks to BannerHelpTricks and show in applyPresetCollectionDefaults
- add if ( check4This( `fpsInitRender=true` ) === true )   in runFPSSuperOnInit

## 1.0.182 - 2023-May-05: setQuickLaunchTransp, fix _addParamToUrl binding
- bump fps-styles to @mikezimm/fps-styles": "^1.0.23
- add setQuickLaunchTransp to src/components/molecules/FullPageBackGround/addCanvasBGImageComponent.ts
- fix logic check:  FPSSlickBackgroundGroup in  https://github.com/mikezimm/Slick-Sections/issues/56

## 1.0.181 - 2023-May-03: fix _addParamToUrl binding
- fix BuildBannerPropsX2 >> addParamToUrl: _addParamToUrl.bind( setup.main ),  this is the proper way to bind it

## 1.0.180 - 2023-May-03: Tweak _allowFullPageBG functionality
- change _allowFullPageBG to type:  IFullBackgroundMode = 'Auto' | 'Partial' | false; -- in IThisFPSWebPartClass and FPSBaseClass
- change default value for _allowFullPageBG = 'Auto'
- change logic in PropPaneHelp and DefaultPropGroups to NOT add elements if NOT 'Auto', so 'Partial' can do those parts differently
- change logic in runSuperOnInit and runWebPartRender to apply stiles if _allowFullPageBG !== false - aka = 'Auto' || 'Partial'

## 1.0.179 - 2023-May-03: addParamToUrl & FullPageBackGround from Slick-Sections
- add new component:  FullPageBackGround to src/components/molecules/FullPageBackGround
- bump fps-styles to v1.0.22 which has the required css files for this component

- Updates to:  src/banner/FPSWebPartClass/IThisFPSWebPartClass.ts
-   add function type interface ICallbackAddParamToUrl
-   update interface: IThisFPSWebPartClass >> add _allowFullPageBG: boolean
-   update interface: IThisFPSWebPartClass >> add _addParamToUrl: ICallbackAddParamToUrl;

- Updates to:  src/banner/FPSWebPartClass/FPSBaseClass.ts
-   add preset: protected _allowFullPageBG: boolean = true; to FPSBaseClass
-   add function:  protected _addParamToUrl( newParamStr:

- Updates to MainWPClass running
-   update runSuperOnInit add line:   if ( thisWPClass._allowFullPageBG === true ) addCanvasBGImageComponent( ... )
-   update runWebPartRender add line:   if ( thisWPClass._allowFullPageBG === true ) addCanvasBGImageComponent( ... )

- change Group name from FPSSlickBackgroundProps to FPSSlickBackgroundGroup
- add group: FPSSlickBackgroundGroup by default in:  getAllDefaultFPSFeatureGroups

- Updates to BannerProps and related
-   extend IMinWPBannerProps with IFPSPageBGWPProps                         >> in src/banner/interfaces/MinWP/IMinWPBannerProps.ts

- Updates to:  src/banner/mainReact/IWebpartBannerProps.ts
-   add to IWebPartBannerProps (aka bannerProps ): addParamToUrl: ICallbackAddParamToUrl;
-   add to IWebPartBannerProps (aka bannerProps ): fpsPageBGWPProps: IFPSPageBGWPProps;

-   add prop:  addParamToUrl to const bannerProps: IWebpartBannerProps = {  >> in src/banner/FPSWebPartClass/BuildBannerPropsX2.ts
-   add fpsPageBGWPProps: { .... with all WPProps into bannerProps

- add changeFullBackground into exportFPSAnalytics

- Files/Functions added to src/components/molecules/FullPageBackGround/
-   create addCanvasBGImageComponent - main function to update background styles
-   create paramLinks and createParamLink in src/components/atoms/Links/CallBackLinks.tsx  !!!NOTE:  FileName was Capitalized here (was not before)
-   create forceWebpartWhiteText to update text colors in src/components/molecules/FullPageBackGround/forceWebpartWhiteText.ts
-   create UrlParamters ( used with paramLinks ) for FullPageBackground components in src/components/molecules/FullPageBackGround/FullPageBGParams.tsx
-   create IFPSPageBGWPProps ( extends MainWPProps ) for this feature in in src/components/molecules/FullPageBackGround/IFPSPageBGWPProps.ts
-   create PropPaneHelp:  CSSPerformance, CSSWarning, FullImage ... in src/components/molecules/FullPageBackGround/PropHelp/CSSPerformance.tsx
-   create PropPaneGroup: FPSSlickBackgroundGroup in src/components/molecules/FullPageBackGround/PropPane/FPSSlickBackgroundGroup.ts


## 1.0.178 - 2023-Apr-19: WebPartContextCopy_15_2, Slick-Sections
- add bannerPillShape to BannerTheme functionality - near hoverEffect, in IMinBannerThemeProps and various places
- add transparentBlack && transparentWhite to bannerThemes and bannerThemeChoices
- update indexes in bannerThemeChoicesWSiteTheme
- add _instanceId to WebPartContextCopy_15_2

## 1.0.177 - 2023-Apr-17: gitRepoSlickSections
- add gitRepoSlickSections
- add för to PrepositionWords 

## 1.0.176 - 2023-Apr-12: check4This
- add more makeTricks rows:  filtered, itemPaneProps, tracePerformance, fpsInitRender
- add to getFilteredV1:  if ( check4This( 'filtered=true' ) === true )
- revise console.log to use check4This in more places


## 1.0.175 - 2023-Apr-12: Misc
- "@mikezimm/fps-pnp2": "^1.0.43" - check4This update for =false params
- comment out console.log in buildWordSummary https://github.com/mikezimm/Compliance/issues/177
- add more console.log to src/components/molecules/HTTP/HttpFetch/functions.ts

## 1.0.174 - 2023-Apr-11: HelpPanel Double Performance
- modify getFullPanel to remove extra performance panel

## 1.0.173 - 2023-Apr-11: HelpPanel Double Performance
- adding text to trace the double table

## 1.0.172 - 2023-Apr-11: HelpPanel Double Performance
- adding text to trace the double table

## 1.0.171 - 2023-Apr-11: buildWordSummary, PrepositionWords
- update buildWordSummary to include exclusionsLC for:  https://github.com/mikezimm/Compliance/issues/173
- add 'this' to PrepositionWords

## 1.0.170 - 2023-Apr-11: tricksTable _panelVersion, Suggestion exclusions
- update tricksTable in ReusaableTricks to use functions from components/SingleHelpPage/makeTricksTable
- update DefaultEasyPagesTabs to start with 'Shortcuts'
- update ProductWords in eiTypes.ts
- for https://github.com/mikezimm/fps-library-v2/issues/50:
-   add _panelVersion default to FPSBaseClass and IThisFPSWebPartClass
-   add versionDate: string; versionLabel: string; versionInfo: string; to IWebpartBannerProps;
-   add versionDate, versionLabel and versionInfo to bannerProps in mainWebPartRenderBannerSetupX
-   add webpart version to panel - Top and above performance 
- create src/components/atoms/Suggestions/excludePrepositions.ts from https://github.com/mikezimm/Compliance/issues/132
- update getSuggestionsByKeys to now look for exclusions in src/components/atoms/Suggestions/getSuggestionsByKeys.ts

## 1.0.169 - 2023-Apr-11: tricksTable - for check4This
- create createTricksTable in src/banner/components/SingleHelpPage/makeTricksTable.tsx
- create FPSFetchTricks, BannerHelpTricks and other arrays of parameter tricks tied to check4This function

## 1.0.168 - 2023-Apr-11: Suggestions
- update convertSugsLC to Suggs to Finds, auto-remove duplicates
- bump to "@mikezimm/fps-pnp2": "^1.0.41"

## 1.0.168 - 2023-Apr-10: Misc console.log and commenting updates
- fix what looks like comment error in addSearchMeta1
- update addSearchMeta2:  change to if ( check4This( 'addSearchMeta2=true') === true ...
- update getSuggestionsByKeys:  change to if ( check4This( 'suggestions=true' ) === true )


## 1.0.167 - 2023-Apr-05: FPSUser to IZSentAnalytics
- add FPSUser to IZSentAnalytics and saveAnalytics3
- add fetch? and analytics? to IZSentAnalytics

## 1.0.166 - 2023-Apr-05: add performance to functions in pnpjs
- add .refreshId and .loaded to checkAnyResults
- add .status = 'AccessDenied' option to checkItemsResults 
- update performanceSettings op in getFilteredSubSites, getSubSites, getWebInfoIncludingUniqueMin and getWebInfoIncludingUniqueAll

## 1.0.165 - 2023-Apr-05: add performance to functions in pnpjs
- add performance to getWebLists, getFilteredSubs, getSubSites, getFilteredSubSites, getWebInfoIncludingUniqueMin, getWebInfoIncludingUniqueAll
- filter out allItems in check4Gulp in addSearchMeta2

## 1.0.164 - 2023-Apr-05: IExtendedWordObject and IExtendedWordSummary
- make IExtendedWordObject params optional, make array of items
- add performanceR to IExtendedWordSummary

## 1.0.162 - 2023-Apr-05: IExtendedWordObject and IExtendedWordSummary
- add interface IExtendedWordObject and IExtendedWordSummary for Compliance so add related items to word objects

## 1.0.161 - 2023-Apr-05: modifiedAge, createdAge, publishedAge
- add modifiedAge, createdAge, publishedAge to IAnySourceItem in src/components/molecules/SourceList/IAnyContent.ts
- modify addSearchMeta1 > addDateTimeFileInfoSearch to include modifiedAge, createdAge, publishedAge

## 1.0.160 - 2023-Apr-05: FPSAgeHook new Optional prop:  alternateOptions
- added FPSAgeHook new Optional prop:  alternateOptions - can pass in FPSAgeSliderOptions5Years, FPSAgeSliderOptions7Years, FPSAgeSliderOptions10Years

## 1.0.160 - 2023-Apr-03: add viewProps and editProps to standard sources
- update DefaultLibrarySource : add standard viewProps and editProps;
- update SitePagesSource : add standard viewProps and editProps;
- update createMinFetchProps: add standard viewProps

## 1.0.159 - 2023-Apr-03: refactor CustomPanel, ContentPanel
- Move CustomPanel and ICustomPanel (now separate file into subFolder)
- Move ContentPanel and IContentPanel (now separate file into subFolder) - was SourceContentPanel.tsx

## 1.0.158 - 2023-Mar-30: ItemPane and getStringArrayBasic
- update itemPane to accept showHeading and showEmbed paramters
- create ItemPane wrapper for basic (non ModernPage) content:  CustomPanel in src/components/molecules/SourceList/CustomPanel.tsx
- update getStringArrayBasic to split international words better.

## 1.0.157 - 2023-Mar-30: Testing fixes
- add StandardMetaViewProps to src/pnpjs/SourceItems/Interface.ts so it can be used in viewProps

## 1.0.156 - 2023-Mar-30: searchText IModernPagesProps, ModernPages, ContentPanel
- correct goToLinks leftPadding >> now rightMargin
- add searchText?: string; to src/components/molecules/ModernPages/Interfaces/IModernPagesProps.ts
- add searchText?: string; to src/components/molecules/ModernPages/ModernPages.tsx
- add searchText? to ContentPanel calling SingleModernPage

## 1.0.155 - 2023-Mar-30: getHighlightedText when number
- fix getHighlightedText for cases where text is a number.  Also fixing for cases where not a number either but should typically be checked for objects earlier.

## 1.0.154 - 2023-Mar-30: searchText, ISingleModernPageProps
- add optional searchText to ISingleModernPageProps so it can be passed into ItemPane > properties
- searchText to getItemProperties in src/components/molecules/SourceList/ItemPane/component.tsx
- fix some searchText, View and Edit logic in src/components/molecules/SourceList/ItemPane/itemProperties.tsx

## 1.0.153 - 2023-Mar-30: ItemPane stuff
- fix src/components/atoms/Links/GoToLinks.tsx to also look for searchHref ( which is used for site pages )
- add searchText all the way down to ItemPane and ItemProperties to show highglighted text in the item panel
- add optional coluumns to getItemProperties  ( View, Edit and SearchText )
- update  ISourceProps: add viewProps, editProps to( to show in ItemPane )
- update preSourceColumns to handle viewProps, editProps

## 1.0.152 - 2023-Mar-30: ModernPages, SinglePage, SourcePanelContent
- bump fps-styles to 1.0.20
- fix css reference to @mikezimm/fps-styles/dist/ModernPages.css ->> ModernPages with an S at the end :)
- create getDateStampRow function in: src/components/atoms/WhoDunItRow/getDateStampRow.tsx
- create getGoToLinks function in: src/components/atoms/Links/GoToLinks.tsx
- create getItemEmbed in: src/components/molecules/SourceList/ItemPane/itemEmbed.tsx
- update to use new Functions: ItemPane/Component.tsx, LimitedVersion.tsx, SinglePage/PageDetails.tsx, SinglePage/SingleModernPage.tsx
- update addDateTimeFileInfoSearch to add: item[ 'Author/Title', 'Author/Name', 'Editor/Title', 'Editor/Name', ]
- add showProperties to ItemPaneProps to show by default but give option to hide

## 1.0.151 - 2023-Mar-30: ModernPages, SinglePage, SourcePanelContent
- remove src/pnpjs/SourceItems/index.ts
- remove src/pnpjs/index.ts
- migrate src/components/molecules/SourceList/SourcePanelContent.tsx from ALVFinMan
- update css in src/components/molecules/SourceList/ItemPane/component.tsx to use fpsGeneralCSS instead of one thing from sourceItemPane.css
- migrate src/components/molecules/ModernPages/... from ALVFinMan
- fix imports to removed indexes

## 1.0.150 - 2023-Mar-30: Suggestions and Words
- create getStringArrayBasic in src/logic/Strings/getStringArrayBasic - similar logic was used both in Words and Suggestions
- modify getArrayOfWordsFromString to use getStringArrayBasic since that logic was in multiple places
- update getSuggestionsFromStrings to use common function to get words from strings ( getStringArrayBasic ) - src/components/atoms/Suggestions/getSuggestionsByKeys.ts
- added some common regex constants for easier reference which were used in getStringArrayBasic

## 1.0.150 - 2023-Mar-28: PersonaCard and SearchBoxRow css fixes
- fix docCardClass in PersonaCard.tsx to properly show theme color if provided
- fix css require in src/components/molecules/SearchPage/component/SearchBoxRow.tsx

## 1.0.149 - 2023-Mar-28: PersonaCard, PersonaRow, Suggestions, WordSummary, SourceSearchHook etc from Compliance and ALVFM
- add PersonaCard and PersonaRow from Compliance to src/components/atoms/PersonaCard <<< NEED TO VERIFY >>>
- add Suggestions logic, interface and samples from Compliance to src/components/atoms/Suggestions <<< NEED TO VERIFY >>>
- add WordSummary from Compliance to src/components/atoms/WordSummary/ <<< NEED TO VERIFY >>>
- add getWordsFromString and related functions from Compliance to src/logic/Strings/getWordsFromString
- add SourceSearchHook from Complaince to src/components/molecules/SearchPage/component/SearchBoxRow
- add ISourceInfo from Compliance to src/pnpjs/SourceItems/Interface
- add getFiltered from Compliance to src/components/molecules/SearchPage/functions/getFilteredV1
- add SourceList ItemPane from ALVFinMan to src/components/molecules/SourceList/ItemPane/component

## 1.0.149 - 2023-Mar-26: month date labels and pref language
- fix casing of return in getFPSPrefNavLang since all are supposed to be LC.

## 1.0.148 - 2023-Mar-26: month date labels and pref language
- add getMonthStr3Array, getMMMDDFromDate and getMMMDDFromStr to src/logic/Time/monthLabels.ts
- add getMonthStrArray, getFullMonthStrFromDate and getFullMonthStrFromDate to src/logic/Time/monthStrings.ts

## 1.0.147 - 2023-Mar-26: month and day labels
- add IFPSDateLanguageObject as object interface for monthStr3 and weekday3
- moved monthStr to src/logic/Time/monthStrings (from monthLabels)
- created monthStr with original keys also in src/logic/Time/monthStrOldKeys

## 1.0.146 - 2023-Mar-20: Various
- add fileSizeNumber to IFPSFileObject in src/pnpjs/SourceItems/FileInterface and addSearchMeta1
- update getHighlightedText for error when text === undefined

## 1.0.145 - 2023-Mar-20: Various
- update getSizeLabel to account for 1024 bits per byte
- update IContentGroup options: ContentGroupFolder: IContentGroup = 'Folder';  ContentGroupOther: IContentGroup = 'Other';
- change itemIsFolder to itemIsFolderContent in src/components/molecules/SourceList/IAnyContent.ts
- add docm to StdFileSearchTypes in src/components/molecules/SearchPage/Interfaces/StandardTypes.ts

## 1.0.144 - 2023-Mar-20: SearchTypes
- refactor addItemIsA to simplify code ( put updates in if item.meta .... )
- update addSearchMeta2 - map item.allIsAKeys into meta in case it was not already added
- change ItemIsDataContent from xml file to json in components/molecules/SearchPage/Interfaces/ProgrammingFileKeys.ts
- refactor mergeWordArrays to use spread to avoid using direct reference to array.

## 1.0.143 - 2023-Mar-20: SearchTypes
- add to IAnySourceItem: primarySearchType: ISearchType; searchTypes: ISearchType[]; allIsAKeys: IItemIsAValues[];
- add to ISearchType: isAKeys: IItemIsAValues[];  update all default constants
- change MediaGroupOffice to ContentGroupMedia
- update addSearchMeta2 to add item.primarySearchType, searchTypes, allIsAKeys
- reduce 'Invalid searchTypeIdx not found:' by filtering out api ones from Compliance web part

## 1.0.142 - 2023-Mar-20: SearchTypes
- update ItemIsAValues to be consistent:  
    export type IItemIsAValues = 'DocSetItem' | 'FileItem' | 'FolderItem' | 'PageItem' | 'NewsItem' | 'NewsLinkItem'

## 1.0.141 - 2023-Mar-20: SearchTypes
- add object to IAnySourceItem item.searchType = SearchTypes.objs[searchTypeIdx]; in addSearchMeta2
- create ALLProgrammingFileKeys for normal plus XKeys... add to addItemIsA function for ItemIsCodeContent

## 1.0.140 - 2023-Mar-19: SearchTypes
- add forgotten values to ItemIsAKeys in src/components/molecules/SourceList/IAnyContent.ts
- update addSearchMeta2 to properly use ItemIsAKeys
- add contentGroup to OneNote search type

## 1.0.139 - 2023-Mar-19: SearchTypes
- move 'folder' into "StdFileKeys" 
- add additional ItemIs${contentGroup}Content via src/components/molecules/SearchPage/functions/addItemIsA.ts
- change ProgrammingSharePoint to ProgrammingFile in addItemIsA and related places

## 1.0.138 - 2023-Mar-19: SearchTypes
- add contentGroup to ISearchType so it's easier to summarize types of files


## 1.0.137 - 2023-Mar-19: SearchTypes
- add ProgrammingSharePointKeys and ProgrammingSharePointSearchTypes: "js", "html", "css", "json", "xml", "exe", "ps1"
- add XProgrammingSharePointKeys and XProgrammingSharePointSearchTypes: "ts", "md", "py", "vba"
- create ProgrammingSharePointKeys, ProgrammingSharePointSearchTypes, MAXSearchTypes to src/components/molecules/SearchPage/Interfaces/ProgrammingFileKeys.ts
- change order of keys/obj in SearchTypes - moved MediaFileKeys and MediaFileSearchTypes to end
- add ItemIsCode and itemIsCode IAnySourceItem and also addOtherIsAMeta

- #51 fix addSearchMeta1:  item.FileSystemObjectType !== 1 && 
- add item.searchTypeIdx = searchTypeIdx; in addSearchMeta2 ( forgot )


## 1.0.136 - 2023-Mar-19: SearchTypes
- add color, similarKey and warning to ISearchType in src/components/molecules/SearchPage/Interfaces/StandardTypes.ts
- added eXTreme Storage file types/icons to StandardTypes
- reorganized StdFileSearchTypes into StdFileSearchTypes and MediaFileSearchTypes
- update IAnySourceItem to have both typeIdx (original === adjusted) AND searchTypeIdx which is the actual index
- update addSearchMeta2 to save original typeIdx AND searchTypeIdx.

## 1.0.135 - 2023-Mar-19: Remove BaseType from Items, addItemIsA
- create addItemIsA function and update addSearchMeta1 function
- remove BaseType because it does not exist on items.

## 1.0.134 - 2023-Mar-19: IDefaultUser, Sources, addSearchMeta1, IAnyContent, searchTextLC
- add folderString and folderTree to src/components/molecules/SearchPage/functions/addSearchMeta1.ts
- add automatically BaseType FileInterface, ModernSitePagesColumns and to all sourceProps in src/pnpjs/SourceItems/createMinFetchProps.ts
- add 10 itemIsA... props to IAnyContent src/components/molecules/SourceList/IAnyContent.ts
- add 10 itemIsA... props item.FPSItem.Search.searchTextTextLC

- add performanceSettings to all generic Sources - Files, News, SitePages, NewsLinks
- add 'ContentType/Name' to libraryColumns in src/pnpjs/SourceItems/FileInterface.ts
- add docset and folder to StdFileSearchTypes in src/components/molecules/SearchPage/Interfaces/StandardTypes.ts
- update addSearchMeta1 to include folder and docSet icons, also add folder parent url to searchDesc
- update IFPSFileObject with user interface


## 1.0.133 - 2023-Mar-17: IPagesContent, IFPSFileObject, IStateSource, etc
- migrate IPagesContent and IPagesContentFull from ALVFM to src/pnpjs/SourceItems/SitePages/IPagesContent.ts
- migrate IStateSource from Compliance to src/pnpjs/Common/IStateSource.ts
- update IAnySourceItem - add HasUniqueRoleAssignments? boolean;
- update libraryColumns - remove duplicate strings
- create IFPSFileObject in src/pnpjs/SourceItems/FileInterface.ts

## 1.0.132 - 2023-Mar-16: ComplianceOps updates 
- create getArrayOfWordsFromString, mergeArrayOfWordsFromString in src/logic/Strings/getWordsFromString.ts

- create WebUrlHook in src/components/molecules/WebUrlBox
- create HTTPApiHook in src/components/molecules/HTTP/HttpApiBox/component.tsx
- create fetchAPI in src/components/molecules/HTTP/HttpFetch/functions.ts
- create createLibrarySource in src/pnpjs/SourceItems/createLibrarySource.ts
- create createSeriesSort in src/pnpjs/SourceItems/createOrderBy.ts

## 1.0.131 - 2023-Feb-25: checkAnyResults AccessDenied
- update checkAnyResults to set status to 'AccessDenied' instead of just 'Error'

## 1.0.130 - 2023-Feb-16: EasyPages, ILoadPerformanceOps
- add msGraphClientFactory?: any; to WebPartContextCopy_15_2 for calling graph
- update ILoadPerformanceOps -- to add specific ones for User, Web, Site, List (for fetch, analyze, process, save)
- add optional linkFormat and linkeSize to EasyPagesPageHook to give optional formatting if using Pivots directly above it.

## 1.0.129 - 2023-Feb-16: EasyPages EasyIcons
- add optional fpsItemsReturn to EasyPagesHook props - use prefetched items for component if provided
- create addEasyIcons from getPagesContent so it can be re-used separately from easy pages
- move all default EasyIcons to separate file.
- update addStandardSearchArrays & buildItemSearchArray to add OverflowTab

## 1.0.128 - 2023-Feb-16: tricky Constants
- add allCompliance to tricky Constants

## 1.0.127 - 2023-Feb-13: addSearchMeta1
- fix filename:  addSourceMeta1 to addSearchMeta1 (was typo)

## 1.0.126 - 2023-Feb-13: addSearchMeta1
- verify item.meta in buildItemSearchArray and then add all found keywords into that array

## 1.0.125 - 2023-Feb-13: addSearchMeta1
- improve addSearchMeta1:  refactor into functions - addStandardSearchArrays and addStandardSearchArrays

## 1.0.124 - 2023-Feb-13: SearchPage and Teaching Bubbles
- Updates to components/molecules/SearchPage:
-   create addDateTimeFileInfoSearch, addSearchMeta1, addSearchMeta2 in SearchPage - tied with IAnySourceItem
-   create SearchTypes object
-   create ISearchObject, ISearchBucket, ISourceSearch
- Add NewsLinksSource and NewsSource - similar to SitePagesSource
- fix getTeachBubbles

## 1.0.123 - 2023-Feb-11: Teaching Bubbles and build performance right into getSourceItems
- add getTeachBubbles for Teaching Bubbles
- update AllTeachBubbles sample
- update makeBubbleElementFromBubbles to not error out when TeachBubbleArray.length === 0
- add op?: ILoadPerformanceOps; to IPerformanceSettings which is used to trigger the updates in 1.0.122

## 1.0.122 - 2023-Feb-09: build performance right into getSourceItems
- create IPerformanceSettings in src/components/molecules/Performance/IPerformanceSettings.tsx
- add performanceSettings: IPerformanceSettings; to IMinSourceFetchProps
- add performanceOp?: IPerformanceOp; to IFpsErrorObject 
- create startPerformOpV2 and updatePerformanceEndV2 which do performance if it's defined in IMinSourceFetchProps
- add performanceOp into getSourceItems if it's part of sourceProps

## 1.0.121 - 2023-Feb-09: Compliance, ALVFM
- update IFpsErrorObject and checkItemsResults to include:  loaded & refreshId... can now be dropped right into state :)

## 1.0.120 - 2023-Feb-09: Compliance, ALVFM
- create StdFileKeys, StdFileSearchTypes in src/components/molecules/SearchPage/StandardTypes
- create StdSharePointKeys, StdSharePointSearchTypes in src/components/molecules/SearchPage/StandardTypes

## 1.0.119 - 2023-Feb-09: Compliance, ALVFM
- migrate ISearchType and ISearchTypes to src/components/molecules/SearchPage/ISearchTypes from ALVFinMan

## 1.0.118 - 2023-Feb-09: PivotTiles
- add libraryColumnsMeta from libraryColumns but for PivotTiles MetaInfo property

## 1.0.117 - 2023-Feb-09: Compliance / ALVFinMan:  ISource Stuff
- updated ISourceProps to use generic OthersTab,
- added SitePagesSource, ModernSitePagesColumns, ModernSitePagesSearch src/pnpjs/SourceItems/SitePages/SitePagesSource

- refactored EasyPagesSourceProps to use ISourcePropsEP which extends ISourceProps and adds the EasyPagesOverFlowTab
    NOTE:  These were moved from epTypes and ALVFinMan ISource files to new common location

- move ModernSitePagesColumnsPivotTiles, createPivotTilesPagesSource to src/pnpjs/SourceItems/SitePages/createPivotTilesPagesSource
- create IAnySourceItem ( based on ALVFinMan IAnySource) in src/components/molecules/SourceList/IAnyContent.ts
- add libraryColumns to src/pnpjs/SourceItems/FileInterface.ts from ALVFinMan/ISource

- shortened gitRepoCompliance desc to just Compliance Ops

## 1.0.116 - 2023-Feb-08: Compliance
- add gitRepoCompliance to LinksRepos

## 1.0.115 - 2023-Feb-07: Pivot Tiles Various
- add typing to makePropDataText, makePropDataToggles, makePropDataSliders in src/banner/propPane/controls.ts

## 1.0.114 - 2023-Feb-06: Pivot Tiles Various
- add NOEnableVersioning Icon for Pivot Tiles and Easy Contents

## 1.0.113 - 2023-Feb-06: Pivot Tiles Various
- created PresetIntranetBanner for PivotTiles and others

## 1.0.112 - 2023-Feb-03: Pivot Tiles Various
- fix IMinFetchListProps export in getWebLists?

## 1.0.111 - 2023-Feb-03: Pivot Tiles Various
- remove BannerImageUrl.Url from ModernSitePagesColumnsPivotTiles
- standardize RequireCheckout >> ForceCheckout in iconNames to be consistant with EasyContents icon
- add iconNames:  EnableModeration and DraftVersionVisibility
- clean up standardEasyContents.tsx and standardPivotTiles.tsx
- add check4Gulp in /logging/saveAnalytics.ts
- update createIUserFromUser to merge original user object so it carries all existing props on the object.

## 1.0.110 - 2023-Feb-03: Pivot Tiles Groups
- update createIUserFromUser to merge { ...{Original}, ...{NEW}}

## 1.0.109 - 2023-Feb-03: Pivot Tiles Groups
- add optional filter to getAllSiteGroups function

## 1.0.108 - 2023-Feb-03: Pivot Tiles Groups
- fix ModernSitePagesColumnsPivotTiles
- add includeNormal: boolean = true to getSelectColumns
- add Id to getSelectColumns base columns by default (in case it's forgotten)
- add logic for quotes around buildFilterBatches items to filter on like Title eq "Text in quotes"

## 1.0.107 - 2023-Feb-03: Pivot Tiles Groups
- re-export IMinFetchListProps from fps-Pnp2
- add ISiteGroupInfo from Pnp to IGroupResults

## 1.0.106 - 2023-Feb-01: Pivot Tiles Permissions
- change fetchSiteInfo back to getSiteInfo
- moved - buildFilterBatches to fps-library-v2
- add getSiteGroupsInBatch based off of getSiteUsersInBatch

## 1.0.105 - 2023-Jan-30: Pivot Tiles Permissions
- add getSiteInfo - src/pnpjs/Sites/fetchSiteInfo
- add IFpsGetSiteReturn - src/pnpjs/Sites/IFpsGetSiteReturn
- add getWebInfoIncludingUnique/+Min - src/pnpjs/Webs/getWebInfoIncludingUnique
- add IFpsGetWebReturn/+Min - src/pnpjs/Webs/IFpsGetWebReturn

## 1.0.104 - 2023-Jan-30: Pivot Tiles Permissions
- add savePermissionHistory in src/pnpjs/Logging/permissions
- add savePermissionAnalytics in src/pnpjs/Logging/permissionsSave
- add fetchAnalytics in src/pnpjs/Logging/fetch

- add getListRoleAssignments in src/pnpjs/Permissions/getListPerms
- add getWebRoleAssignments in src/pnpjs/Permissions/getWebPerms
- add getUserListRoleAssignments in src/pnpjs/Permissions/getUserListPerms
- add getUserWebRoleAssignments in src/pnpjs/Permissions/getUserWebPerms
- add IFpsRoleAssignmentInfo  in src/pnpjs/Permissions/IFpsRoleAssignmentInfo

- add getSourceItemsWithUniquePerms in src/pnpjs/SourceItems/getSourceItemsUniquePerms
- add getSourceItemsInBatches in src/pnpjs/SourceItems/getSourceItemsBatch
- add getUserListRoleAssignmentsInBatch in src/pnpjs/Permissions/getUserListPermsBatch
- add getUserWebRoleAssignmentsInBatch in src/pnpjs/Permissions/getUserWebPermsBatch
- add getSiteUsersInBatch in src/pnpjs/Users/calls/getSiteUsersBatch
- create buildValueUserInfos - moved code out of getSiteUsers and getSiteUsersInBatch


## 1.0.103 - 2023-Jan-26: Pivot Tiles SourcePages
- add getPivotTilesPagesSource and ModernSitePagesColumnsPivotTiles version of Modern Site Pages columns

## 1.0.102 - 2023-Jan-26: Pivot Tiles hubsFetch testing
- npm install @mikezimm/fps-pnp2@1.0.32

## 1.0.101 - 2023-Jan-26: Pivot Tiles getLists
- add getWebLists in src/pnpjs/Lists/getList/getWebLists.ts

## 1.0.100 - 2023-Jan-26: Pivot Tiles System Lists and Pages
- migrated src/pnpjs/Lists/getList/SysLists.ts
- migrated src/pnpjs/SourceItems/SystemPages.ts
- added LowerCase arrays for system lists and pages as well for easier filtering

## 1.0.99 - 2023-Jan-21: Pivot Tiles Sites and Webs functions
- add departmentId: string to LegacyPageContextCopy_15_2;
- add await to getAssociatedGroups function calls
- create getSubSites in src/pnpjs/Webs/getSubSites
- create getFilteredSubSites src/pnpjs/Webs/getFilteredSubs
- create getAssocSites in src/pnpjs/Hubs/getAssocSites

## 1.0.98 - 2023-Jan-21:
- add gitRepoPowerSearch to RepoLinks

## 1.0.97 - 2023-Jan-16:
- add gitRepoALVSearch to RepoLinks

## 1.0.96 - 2023-Jan-16:  Pivot Tiles various updates
- add buildPivotStylesGroup
- change from Class to exports:  src/common/Pivots/PivotOptions.ts
- add Jira Icon link src/components/atoms/SVGIcons/JiraIcon.ts
- add PivotPropGroup src/common/Pivots/PivotPropGroup.ts

## 1.0.95 - 2023-Jan-14:  Pivot Tiles getUrlVars update
- created getUrlVarsAsObject - new function based on Pivot Tiles funciton that returns an object
- changed getUrlVars to getUrlVarsAsStrings -- because that was different than returning as an object

## 1.0.94 - 2023-Jan-14:  Team T Script Editor
- add gitRepoTeamT

## 1.0.93 - 2023-Jan-13:  Pivot Tiles Groups and GroupUsers
- add isGuestUser, addIsGuestToUsers functions to src/pnpjs/Users/logic/checkIsGuest

## 1.0.92 - 2023-Jan-13:  Pivot Tiles Groups and GroupUsers
- add folder:  src/pnpjs/Groups
- add groups interfaces src/pnpjs/Groups/IFpsAssociatedGroupsReturn
- add group functions: getAllSiteGroups, getAssociatedGroups,
- add group functions: getAssociatedOwnerGroup, getAssociatedMemberGroup, getAssociatedVisitorGroup
- add group functions: getAllUsersFromGroup, getAllUsersFromGroupId, getAllUsersFromGroupName

## 1.0.92 - 2023-Jan-10: Pivot Tiles - migrate ReactImage Props and Prop Pane Choices
- from src/Services/PropPane/ReactImage/v2 to src/common/Images

## 1.0.91 - 2023-Jan-10: SecureScript supportedContacts
- updated importBlockPropsFPS:  added 'supportContacts', 'documentationLinkDesc', 'documentationLinkUrl',
-    so that if you export/import, it updates the SupportContact to current user and makes them update docs info.
- updated download error due to unmanaged device to friendly errors:  https://github.com/mikezimm/SecureScript7/issues/67
- updated checkDeepProperty to allow suppressing console on errors.  https://github.com/mikezimm/drilldown7/issues/316

## 1.0.90 - 2023-Jan-10: Drilldown Prop Pane Help supportedContacts
- added console.log whenever onFPSPropPaneClosed automatically updates supportContacts
- updated onFPSPropPaneClosed to put correct email, name and imageUrl in the prop pane props

## 1.0.89 - 2023-Jan-10: Drilldown Prop Pane Help supportedContacts
- https://github.com/mikezimm/SecureScript7/issues/98
- add onPropertyPaneConfigurationComplete to Class
- create onFPSPropPaneClosed which could be called at any time from web part


## 1.0.87 - 2023-Jan-10: Drilldown Prop Pane Help escape fixes
- numerous places:  replaced escape() with string literals.

## 1.0.86 - 2023-Jan-07: Drilldown Various updates
- update PinMeGroup to not expand:  https://github.com/mikezimm/drilldown7/issues/304
- add spHttpClient?: any; to WebPartContextCopy_15_2 for typing in SecureScript7 for prop pane calls
- update npm install @mikezimm/fps-styles@1.0.13 for drilldown styles
- update npm install npm install @mikezimm/fps-pnp2@1.0.29 for improved error handling for returning common errors like no listName etc..

## 1.0.85 - 2023-Jan-05: Drilldown HelpPanel updates
- update propPaneHelp escaped strings that look funny in page:  https://github.com/mikezimm/drilldown7/issues/289

## 1.0.84 - 2023-Jan-05: SecureScript define PageContext subclasses
- create check4Tricks to standardize checking for showTricks in here and in web part
- added to PageContextCopy_15_2 for better typing ability
    list: PageContextCopy_15_2_List;
    user: PageContextCopy_15_2_User;
    web: PageContextCopy_15_2_Web;
    site: PageContextCopy_15_2_Site;
    cultureInfo: PageContextCopy_15_2_CulturInfo;

## 1.0.83 - 2023-Jan-04: SecureScript IFPSWindow
- add to IFPSWindow: _spPageContextInfo?: LegacyPageContextCopy_15_2;
- add to IFPSWindow: _pageContextInfo?: PageContextCopy_15_2;

## 1.0.82 - 2023-Jan-04: Banner updates
- fix Banner Panel default tab to be OOTBHelpPanel
- add createWhyRow for the Whyme page

## 1.0.81 - 2023-Jan-03: ALVFinMan components
- added makeBubbleElementFromBubbles, IMinTeachBubble to src/components/atoms/TeachBubble
- refactored bubbles to include content element
- Add FadeCarousel and SelectDots under src/components/molecules/FadeCarousel ( from test-fps-test/ALVFinMan web part )
- relocated thinArray and getSpreadIndexes to src/logic/Arrays/thinOutArray.ts
- created getWhoDunItElements in src/components/atoms/WhoDunItRow/getWhoDunIt.tsx to build Peope/Dates row

## 1.0.80 - 2022-Dec-31: clean up console.logs, ALVFinMan fetches
- remove unneccessary console.logs
- fix a couple check4Gulp imports that pull in pnp2
- update PinMeGroup to only auto-expand on PageInfo for now
- add getNextIndex function from FadeCarousel component to src/logic/Arrays/searching/getNextIndex.ts
- update getSourceItems to automatically create expandColumns from selectColumns if it is empty - ALVFinMan
- add fetchFpsPageAsXML and fetchFpsItemAsXML to fetch Modern Page content

## 1.0.79 - 2022-Dec-23: fetch attacments pnpv2 update
update fetch attachments from issue:  https://github.com/mikezimm/drilldown7/issues/302

## 1.0.78 - 2022-Dec-23: friendly error, Theme, ListView
- update friendly error message for to many lookup columns in query:  https://github.com/mikezimm/drilldown7/issues/204
- set default Theme to allow Site Theme:  _allowSiteThemeChoice: boolean = true;
- add iconFieldName to ReactListView if isLibrary

## 1.0.77 - 2022-Dec-23: easyPagesAudience, parentListURL
- easyPagesAudience default Audience:  Page Editors:  
- https://github.com/mikezimm/fps-library-v2/issues/35
- standardize propertyNames in library: https://github.com/mikezimm/fps-library-v2/issues/36
- webURL >> webUrl, listName >> listTitle, parentListURL >> listUrl

## 1.0.74 - 2022-Dec-23: orderByBoolean
- fix orderByBoolean in getSourceItems
- add audience targetting on EasyPages 1.0.74 just enabled the prop pane field

## 1.0.72 - 2022-Dec-23: Fix Endless imports
- fix endless @pnp/sp imports:  https://github.com/mikezimm/fps-library-v2/issues/34
- found in:  src/components/molecules/FieldPanel/components/fetch/funcions.ts


## 1.0.71 - 2022-Dec-23: Help and ...
- change StringFunctions help page to show DoNotFetchSpecial not DoNotFetchSpecialLC
- alternate easyPages and Settings, not both at the same time https://github.com/mikezimm/fps-library-v2/issues/32
- add 'last ditch' friendly message in src/logic/Errors/friendly.ts

## 1.0.70 - 2022-Dec-23: Drilldown String Functions Prop Pane Help
- update StringFunctions prop pane help page to list DoNotExpandTrimSpecial columns
- update all pnpjs getters with more standardized interfaces
- moved getSourceItems to use one from this library and call fetchAnyItems
- standardize the error info building and result interfaces

## 1.0.69 - 2022-Dec-23: Drilldown String Functions, Special Functions
- add getLetterBucket5 for https://github.com/mikezimm/drilldown7/issues/140
- add string Functions:  FirstInFirst5Buckets, FirstInLast5Buckets for https://github.com/mikezimm/drilldown7/issues/286
- add following for https://github.com/mikezimm/drilldown7/issues/294
- add Special Fields/Props:  IDoNotFetchSpecial = 'ModDateFirstName' | 'ModDateLastName' | 'ModDateInitials' | 'ModDateFirstL' ;
- add Special Fields/Props:  IDoNotFetchSpecial = 'CreateDateFirstName' | 'CreateDateLastName' | 'CreateDateInitials'  | 'CreateDateFirstL';
- add function getSpecialColumns:  src/pnpjs/Lists/getVX/getSpecialV2.ts 

## 1.0.68 - 2022-Dec-23: getPreConfig and PivotOptions
- add src/common/Pivots/PivotOptions.ts from Drilldown, should be used with PivotStyle choices (like in PivotTiles)
- add src/pnpjs/PreConfigItems/getPreConfig.ts from Drilldown which gets preconfig settings from PreConfigSite

## 1.0.67 - 2022-Dec-23: reactListView
- bring richTextHeight from Drilldown directly into reactListView
- move fetchAttachments function into separate functions under pnpjs folder
- fix some imports that were to general pulling in more than neccessary

## 1.0.66 - 2022-Dec-22: analytics
- update saveAnalytics: use saveThisLogItemAsync with await, add RuleBreak to IFPSResultStatus again

## 1.0.63 - 2022-Dec-22: analytics
- update saveAnalytics: alert & console.log error to show friendly error when gulping

## 1.0.61 - 2022-Dec-22:  fix bannerEleClasses
- reactListView.tsx:  const bannerEleClasses = ['quickCommandFooterStyles', commandResult ? 'quickCommandShow' : 'quickCommandHide' ];
- reactListView.tsx:  added footerElement from Drilldown for quickCommand results.

## 1.0.60 - 2022-Dec-22:  fix getListProps, fix quickCommands, bring result footer to list component
- fixed createIUserFromUser:  User.Id was getting changed from string to number causing any QuickCommand logic using === to fail on Id check.
- rebuild reactListView.tsx:  createPanelButtons to createPanelButtonsV2 - uses arrow function to pass back Item and Command.  No more parsing the element id stuff!
- npm install @mikezimm/fps-styles@1.0.10
- add quickCommand Result Footer direclty in reactListView (instead of passing all that back to parent - aka Drilldown )

## 1.0.59 - 2022-Dec-21:  fix getListProps
- npm install @mikezimm/fps-pnp2@1.0.18
- test reactListView createPanelButtonsV2 - arrow function

## 1.0.59 - 2022-Dec-21:  PinMe behaviour and EasyPages pando style
- add forceSPAStyle to FetchBannerX.tsx and EasyPagesHooks props :  https://github.com/mikezimm/fps-library-v2/issues/24
- add WebPartLinks padding-top on fps-library row

## 1.0.58 - 2022-Dec-21:  FieldPanelMin
- fix FetchBannerX - changed this.props.pinMeState to this._pinMeState, save for pin function.

## 1.0.57 - 2022-Dec-21:  FieldPanelMin
- fix updateFarElementsPinMe fix onClick for when state = pinMini... was pinMini now pinFull so it does actually toggle.
- fps-styles@1.0.10 - 2022-Dec-20: add to overflow-x: hidden; pinMeMini

## 1.0.56 - 2022-Dec-21:  FieldPanelMin
- create FieldPanelMin (minimal field panel page)

## 1.0.55 - 2022-Dec-21:  add PinMe icon and state
- update FetchBannerX to have local variable this._pinMeState and this._updatePinState - either from local or passed in from parent component.
- update updateFarElementsPinMe to have new logic
- resolves https://github.com/mikezimm/fps-library-v2/issues/23

## 1.0.54 - 2022-Dec-21:  library repoLinks in About Panel
- tweak library issues links to 'legacy' so shows as 'fps-styles issues' instead of just 'issues'
- "@mikezimm/fps-styles": "^1.0.9" -> https://github.com/mikezimm/fps-library-v2/issues/13

## 1.0.53 - 2022-Dec-21:  library repoLinks in About Panel
- update:  add libraries to LinksRepos and incorporate new libs into WebPartLinks https://github.com/mikezimm/fps-library-v2/issues/21
- fix:     Fix FetchBannerX and FullPanel to show all contentPages:  https://github.com/mikezimm/fps-library-v2/issues/9

## 1.0.52 - 2022-Dec-21:  reactList && commands columns
- fix:  updateReactListItem and reactListView https://github.com/mikezimm/fps-library-v2/issues/20
- updated PropPaneGroups to not show PinMe or FPSBasics in certain conditions like SPA:   https://github.com/mikezimm/fps-library-v2/issues/7
- fix:  Fix about tab not showing in panel:  https://github.com/mikezimm/fps-library-v2/issues/9

## 1.0.51 - 2022-Dec-19:  reactList && commands columns
- https://github.com/mikezimm/fps-library-v2/issues/12 - updated getSelectV2, getExpandV2, getFuncV2
- https://github.com/mikezimm/fps-library-v2/issues/19 - updated getSelectV2, getExpandV2, getFuncV2

## 1.0.51 - 2022-Dec-19:  reactList && commands issues
- https://github.com/mikezimm/fps-library-v2/issues/11 - fix reactListView to return element if no items
- https://github.com/mikezimm/fps-library-v2/issues/14 - fix Drilldown Commands
- https://github.com/mikezimm/fps-library-v2/issues/15
- https://github.com/mikezimm/fps-library-v2/issues/16


## 1.0.50 - 2022-Dec-19:  reactList
- npm install @mikezimm/fps-styles@1.0.8
- https://github.com/mikezimm/fps-library-v2/issues/11

## 1.0.49 - 2022-Dec-19:  reactList
- add bar styles back in via @mikezimm/fps-styles@1.0.6 and passing in barTheme class same as FetchBannerX

## 1.0.49 - 2022-Dec-19:  expando
- fix const enableExpandoramic in BuildBannerPropsX2 to correctly show pando button

## 1.0.48 - 2022-Dec-19:  site theme
- updated FetchBannerX to accept siteThemes object to better insure that a web part matches options available in that library version

## 1.0.47 - 2022-Dec-19:  site theme
- add following props to BannerProps and IFPSEnviro
  themeChoice: string;
  useSiteTheme: boolean;
- add logic in banner to over-ride banner styling with class provided in main react component
- update createStyleFromString to accept ignoreColors flag to ignore colors from styling

## 1.0.46 - 2022-Dec-19:  reactListView part 2
- fix let parentListFieldTitles = ... error when this is '' - can't JSON.parse it.

## 1.0.45 - 2022-Dec-19:  reactListView part 1
- add items.length check to reactListView


## 1.0.44 - 2022-Dec-18:  Drilldown Update part 5
- remove duplicate src/common/Audiences folder from here.... go to banner/propPane/Audiences instead
- fix reactListView css import to point to fps-sytles

## 1.0.43 - 2022-Dec-18:  Drilldown Update part 5
- add siteServerRelativeUrl to IFPSEnviro - in order to easily tell if a url is on the current site collection

## 1.0.41 - 2022-Dec-18:  Drilldown Update part 4
- delete ILink and replace with ISimpleLink which is same but with optional target
- migrate zPivots from npmFunctions to src/common/interfaces/fps/IzPivots
- migrate IListInterfaces to src/common/interfaces/fps/Picked/IListInterfaces.ts
-       Move to separate files in case needed that way

## 1.0.40 - 2022-Dec-18:  Drilldown Update part 3
- created src/pnpjs/CommandItems/updateItem.ts to update command items (the actual part that just saves using fps-pnpv2)
- standardized return status signatures to IFPSResultStatus https://github.com/mikezimm/fps-library-v2/issues/10
- cleaned up '/index*' references to be more specific

## 1.0.39 - 2022-Dec-18:  Drilldown Update part 2
- move replaceHandleBars from src/logic/Strings/handleBars.ts to /handleBarsContext.ts to
- add fetchCount to "@mikezimm/fps-pnp2": "^1.0.14" for fetching items.
- update updateReactListItem.tsx code to use fps-Pnp2 library to get items

## 1.0.39 - 2022-Dec-17:  Drilldown Update
- npm install @mikezimm/fps-pnp2@1.0.13 >> Has Drilldown fetch and update core function, wrapper function to be here.
- Create ReactList View from Drilldown: src/components/molecules/ReactListV1
- rename handleBars functions

## 1.0.39 - 2022-Dec-17:  Drilldown Update
- Migrate Drilldown PropPaneHelp pages - src/common/PropPaneHelp/pages/listview
- Restructured PropPaneHelp folder into subfolders
- Migrate Drilldown String functions - src/logic/Strings/drillParse
- Create folder for PreConfigProps / SiteCollectionPresets >> src/common/PropPaneHelp/preconfig
- Migrate buildConfirmDialog and buildConfirmDialogBig from Drilldown to src/components/atoms/Elements


## 1.0.38 - 2022-Dec-16:  FieldPanel Update
- add ...changesFieldPanel to exportIgnorePropsFPS
- externalize react-json-view

## 1.0.37 - 2022-Dec-16:  FieldPanel Update
- Update mainWebPartRenderBannerSetupX to properly bind saveViews and saveCommands function
- Update class _saveFieldPanelCommandsFunction and _saveFieldPanelViewsFunction with better logic
- Update PropPaneColsClass _updatePerformance to properly show performance

## 1.0.36 - 2022-Dec-16:  FieldPanel Update
- Add FPSFieldsPanelPropGroup to getAllDefaultFPSFeatureGroups

## 1.0.35 - 2022-Dec-15:  FieldPanel Update
- Rename IFieldPanelProps to IMinWPFieldPanelProps
- Subsitute webURL for webUrl for consistancy across library
- Change components folder from PropPaneCols to FieldPanel which is really what it is
- Add FPSBaseClass:  _allowFieldPanel, _FieldPanelDesignMode, _FieldPanelWebProp, _FieldPanelListProp
- Add saveFields, saveViews functions to class
- Add logic to FieldPanel info to fieldPanelProps, runWebPartRender WP Props to fieldPanelProps
- Reorganize runWebPartRender logic to group similar functions ( Panel, Near, FieldPanel etc... )

## 1.0.34 - 2022-Dec-15
- Updated styles references in PropPaneCols component
- Bumped styles version to 1.0.3


## 1.0.33 - 2022-Dec-15
- Add PropPaneCols component - NEEDS CSS FIXED

## 1.0.32 - 2022-Dec-15
- udpate IFPSEnviro.web.id and .site.id to check for complex id object
- Add EasyPages updates in runOnPropChange from Pnpjs-v2 testing
- Migrate src/zComponents/Accordion_ to components/molecules
- Migrate src/zComponents/Arrows_ to components/molecules


## 1.0.31 - 2022-Dec-15
- migrate saveAnalytics.ts, interfaces and functions
- add SiteID, WebID, SiteTitle to IFPSEnviro

## 1.0.30 - 2022-Dec-15
- Add analyticsProps

## 1.0.29 - 2022-Dec-15
- Changed Const: FPSPinMePropsGroup to Function:  FPSPinMePropsGroupX - to auto-detect enviro
- fix _trickyEmailsALL to _trickyEmailsAll (All lower cased)

## 1.0.28 - 2022-Dec-15
- Create getAllDefaultFPSFeatureGroups to get all FPS Groups in one batch
    Auto-detects which to ignore using thisWPClass options


## 1.0.27 - 2022-Dec-15
- Add trickyEmailsAll to FPSEnviro
- update ReactJSON collapsed depth on PropPanel pages

## 1.0.26 - 2022-Dec-15
- change _allowExpando to _allowPandoramic
- change _disablePandoramic to _allowPandoramic
- change _disablePinMe to _allowPinMe for consistancy of this._properties

- NOTE That this change requires logic check on all PinMe applications since 
    now true means allow vs in past it meant disable

## 1.0.25 - 2022-Dec-15
- Create window.FPSEnviro:  IFPSEnviro using createFPSEnviroOnWindow during runSuperOnInit
- Add FPSEnviro to HelpPanel User tab
- Update PropertyPaneGroups to accept thisWPClass: IThisFPSWebPartClass - make life a LOT easier

## 1.0.24 - 2022-Dec-14
- change _exportIgnoreProps to _exportIgnorePropsWP, webpart only passes it's props.  runFPSInit adds FPS ignores
- change _importBlockProps to _importBlockPropsWP, webpart only passes it's props.  runFPSInit adds FPS ignores
- clean up old comments

## 1.0.23 - 2022-Dec-14
- move consolidate some PropPane files

## 1.0.22 - 2022-Dec-14
- Add baseline files for updated IThisFPSWebPartClass, FPSBaseClass
- Add runFPSSuperOnInit, runFPSWebPartRender, runOnPropChange buildExportPropsX

## 1.0.21 - 2022-Dec-13
- update easyPagesSources - add 'Article' css class and logic based on testing

## 1.0.20 - 2022-Dec-13
- Add EasyPages component to banner

## 1.0.19 - 2022-Dec-13
export { FPSBanner4BasicGroup,  } from './FPSBanner4BasicGroup';
export { FPSBanner3NavGroup, } from './FPSBanner3NavGroup';
export { FPSBanner3ThemeGroup } from './FPSBanner3ThemeGroup';

## 1.0.18 - 2022-Dec-13
- fix this. errors in functional components
- update css import statements

## 1.0.17 - 2022-Dec-13
- update PresetFPSBanner with EasyPages EasyIcons
- migrate updateBannerThemeStyles, refreshBannerStylesOnPropChange to src/banner/features/PageStyle/bannerThemes.ts
- migrate renderCustomStyles to src/banner/features/PageStyle/renderCustStyles.ts
- import PreConfig EasyPages/EasyIcons from Drilldown to src/common/PropPaneHelp/PreConfiguredConstants.ts

## 1.0.16 - 2022-Dec-12
- clean up build errors - moved temp files back to npmFunctions so could build

## 1.0.15 - 2022-Dec-12
- More cleanup imports

## 1.0.13 - 2022-Dec-12
- Target more specific imports instead of just import { ... } from '../../../pnpjs
- was causing web part to suck in entire folder and all dependancies

## 1.0.12 - 2022-Dec-11

### Installs

- npm install react-json-view@1.21.3
- npm install @pnp/spfx-property-controls@3.6.0
- npm install @mikezimm/fps-styles@1.0.1

### Linting - Set these to true and cleaned up warnings

  "strictNullChecks": true,
  "noUnusedLocals": false,
- Turned off noUnusedLocals when done... saved error count to zNotes/Errors - noUnusedLocals
- Keeping strictNullChecks ON for now since I was able to clean all current warnings

### Decamelize 

- Created local version of https://github.com/sindresorhus/decamelize,

- Moved PropPane help pages into separate files:  src/common/PropPaneHelp/pages/FPSCommonOnNpm.tsx
- Moved duplicate Audiences from banner sub-folter to src/common/Audiences

### CommandStyles

- import npmFunctions/src/HelpPanelOnNPM/onNpm/defaults_.ts to /src/common/commandStyles/defaults.ts
- import npmFunctions/src/HelpPanelOnNPM/onNpm/adjustCmdThemes_.ts to /src/common/commandStyles/adjustCmdThemes.ts

### VisitorPanel

- Move VisitorPanelHelp Interfaces to src/banner/components/VisitorPanel/Interfaces.ts
- import npmFunctions/src/CoreFPS/VisitorPanelComponent_.tsx to src/banner/components/VisitorPanel/VisitorPanelComponent.tsx
- import npmFuctions/src/CoreFPS/FPSOptionsGroupVisHelp_ to src/banner/components/VisitorPanel/FPSOptionsGroupVisHelp.ts

### CoreFPS

- import npmFuctions/src/CoreFPS/ReactComponentProps to src/banner/mainReact --- Props and State separated
- import npmFuctions/src/CoreFPS_/BannerPageMisc_.tsx to src/banner/components/Panel/createAboutRow.tsx <<< FILE RENAME >>>

### Gear

- import npmFuctions/src/HelpPanelOnNPM/onNpm/interfaces_.ts to src/banner/components/Gear/IKeySiteProps.ts
- import npmFuctions/src/HelpPanelOnNPM/banner/onLocal/bannerGearFunctions_.tsx to 
- import npmFuctions/src/HelpPanelOnNPM/banner/onLocal/bannerGearFunctions_.tsx to src/banner/components/Gear
- import npmFuctions/src/HelpPanelOnNPM/banner/onLocal/bannerSettings_.css to src/banner/components/Gear

### SpecialBanner

- import npmFuctions/src/HelpPanelOnNPM/specialX to src/banner/components/SpecialBanner

### WebPartLinks

- import npmFuctions/src/HelpPanelOnNPM/banner/onLocal/WebPartLinks_.tsx to src/banner/components/WebPartLinks/WebPartLinks.tsx

### Main Component

- import npmFuctions/src/HelpPanelOnNPM/banner/onLocal/component_.tsx to src/banner/banner/component.tsx
- import npmFuctions/src/HelpPanelOnNPM/banner/onLocal/banner_.css to src/banner/banner/banner.css

### Main Render

- import npmFuctions/src/HelpPanelOnNPM/onNpm/BannerInterface_.ts to src/banner/renderBBP/BannerInterface.ts
- import npmFuctions/src/HelpPanelOnNPM/onNpm/buildBannerPropsV1_.ts to src/banner/renderBBP/buildBannerPropsV1.ts
- import npmFuctions/src/HelpPanelOnNPM/onNpm/Moved_/WebPartRenderBannerV2_.ts to src/banner/renderBBP/WebPartRenderBannerV2.ts

### Others

- import npmFuctions/src/Services/PropPane/StringToReactCSS.ts to src/logic/Strings/reactCSS.ts
- import npmFuctions/src/Services/Navigation/site.ts to src/logic/Links/Navigation.ts
- import npmFuctions/src/Elements_ to src/components/atoms/Elements

- import npmFuctions/ to 

## 1.0.11 - 2022-Dec-11
- redirected all css requires to @mikezimm/fps-styles/dist/samefile.css

## 1.0.10 - 2022-Dec-10
- update getPagesContent based on testing

## 1.0.9 - 2022-Dec-10
- update prepSourceColumns, componentPage based on testing

## 1.0.8 - 2022-Dec-10
- filter duplicate columns in prepSourceColumns
  sourceProps.columns = columns.filter((element, index) => ...;
  sourceProps.selectThese = selectThese.filter((element, index) => ...;
  sourceProps.expandThese = expColumns.filter((element, index) => ...;

## 1.0.6 - 2022-Dec-10
- Add check4Gulp to /pnpv2/SourceItems, add saveErrorToLog to /pnpv2/users functions

## 1.0.5 - 2022-Dec-10
- fixes when turning on tsconfig rules:
    "strictNullChecks": true, ==>> reduced to false after some udpates/fixes
    "noUnusedLocals": true, ==>> reduced to false after some udpates/fixes
    "noImplicitAny": true,

## 1.0.4 - 2022-Dec-10
- npm install @mikezimm/fps-pnp2@1.0.10
- had LOTS of due to single UpperCase Users in src/index.ts
- Error was: multiple modules with names that only differ in casing

## 1.0.4 - 2022-Dec-10
- npm install @mikezimm/fps-pnp2@1.0.9
- Fixed errors in ensureUserHere and ensureUserInfo per below:
- Tried passing in user.user but it errored out all the time.  Now testing for .data first
    const userObject: any = user.data ? user.data : user.user;
    return { user: userObject, e: null, status: 'success' }
- Tested full and relative Urls and relative Urls errored out.  Added
    const fullWebUrl = webUrl.indexOf('https:') === 0 ? webUrl : window.location.origin + webUrl;
    let thisListWeb = Web(fullWebUrl);

## 1.0.4 - 2022-Dec-10
- Change createIUserFromUser to NOT put LoginName in an email property

## 1.0.3 - 2022-Dec-10
- update createIUserFromUser:  better fill in User:  LoginName, Emails, and even Picture Url
- fps-pnp2@1.0.8: update fetchSiteAdmins: add (per testing) - import { IList } from "@pnp/sp/lists";

## 1.0.2 - 2022-Dec-10
- Update createIUserFromUser to find variations of email and login names when not in user object.
- Add Mock sample data object of typical context.pageContext.User and legacyPageConext User info

## 1.0.1 - 2022-Dec-10
- npm install @mikezimm/fps-pnp2@1.0.7:  
  update pnp imports to include required things.  Originally found from testing fetchSiteAdmins

## 1.0.0 - 2022-Dec-09
- completely rebuilt userServices in src/pnpjs/Users
