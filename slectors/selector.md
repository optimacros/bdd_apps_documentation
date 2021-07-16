# Селекторы

| Name Selector  | Class                                          | Tag or any contains   |  Exists attr |
| -------------  | -------------                                  | -------------         |  -------------         |
| global Loader  | GlobalLoader__Overlay                          |                       |                        |
| loader         | LocalLoader__Container                         |                       |                        |
| any Loader     | GlobalLoader__Overlay , LocalLoader__Container |                       |                        |
| search Results | SearchResultList                               |                       | yes                    |
| search Input   | Search__inputElement , FilterInput__Field , SearchButton__Input |      | yes                    |
| modal                | ReactModal__Content                      |                       |                        |
| output Macros Dialog | OutputMacrosDialog-module__Content       |                       |                        |
| modal Color Picker   | Color__picker                            |                       |                        |
| modal Title          | Modal__Header_Title                      |                       | yes                    |
| grid Title           | GridTitle-module__Title                  |                       | yes                    |
| modal Form Content   | ModalFormDialog__InsertModuleDialog      |                       |                        |
| toolbar Of Toolbar Settings | ToolbarSettingsDialogMenu-module  |                       |                        |
| button             |                                            |  button               | yes                    |
| enabled Button     | not class ***Disabled***                   |  button               | yes                    |
| configurator Dnd Element |                                      |  button               | yes                    |
| configurator Dnd Element Button | ProgressBarContainer          |  name                 | yes                    |
| menu Item                | mdl-portalmenu__item  , menuItem , react-contextmenu-item |  | yes                    |
|                          | rc-dropdown-menu-item  , rc-dropdown-menu-submenu         |  |                        |
| grid Context Menu        | gridContextMenu , react-contextmenu  |                       |                        |
| notification             | snackbar                             |                       | yes                    |
| recalculate Notifications | HeaderNotifier__notificationContainer_Title  |              | yes                    |
| recalculate Notifications Title | HeaderNotifier__notificationContainer_Title  |        |                        |
| popup Menu                | mdl-portalmenu__list , rc-dropdown-menu-root  |             |                        |
| grid Comments Editor      | GridCommentsElement__Message        |                       |                        |
| grid Error Dialog         | ErrorDialog__messageContainer       |                       |                        |
| tab Header                | TabHeader__TabButton__              |                       | yes                    |
| tabs Container            | TabsContainer                       |                       |                        |
| main Tabs Header Container| MainTabs__HeaderContainer           |                       |                        |
| Tabs Header Container     | TabHeader__TabHeaderContainer       |                       |                        |
| toolbar                   |                                     | navigation            |                        |
| dashboard Toolbar         | dashboardTabHeader                  |                       |                        |
| toolbar Right Side        | RightToolbarButtons                 |                       |                        |
| validation Error          | error                               |                       |                        |
| tree Menu                 | BaseMenu__Menu , FilterMenu__Container |                    |                        |
| tree Menu Element         | BaseMenu__Element                   |                       | yes                    |
| filter Element            | BaseMenu__Element                   |                       | yes                    |
| tree Menu Title           | TreeMenu__title                     |                       | yes                    |
| tree Menu Arrow           | BaseMenu__ButtonArrow               |                       |                        |
| custom Button Container   | CustomButton-module__Container      |                       | yes                    |
| button Settings           | CustomButton-module__IconContainer  |                       |                        |
| sample Value              | Number__SampleValue , Text-module__SampleValue |            | yes                    |
| tree Element Container    | BaseMenu__ListElement               | name , data-name      | yes                    |
| Drive Landing             | Content__Wrapper                    |                       |                        |
| drive Landing Page        | DriveLanding__Container             |                       |                        |
| header View               | Header__View                        |                       |                        |
| model Item                | ModelsItemRow-module__Container ,   |                       | yes                    |
|                           | ModelsItemCard-module__Container    |                       |                        |
| status Offline            | module__Status_offline              |                       | yes                    |
| folder Item               | FoldersItemRow-module__Container    |                       | yes                    |
|                           | FoldersItemCard-module__Container   |                       |                        |
| model Row                 | ModelsItemRow-module__Container     |                       | yes                    |
| folder Row                | FoldersItemRow-module__Container    |                       | yes                    |
| model Card                | ModelsItemCard-module__Container    |                       | yes                    |
| folder Card               | FoldersItemCard-module__Container   |                       | yes                    |
| create Model Element      | createModelElement                  |                       |                        |
| create Folder Element     | createFolderElement                 |                       |                        |
| clean Temp Models         | cleanTempModels                     |                       |                        |
| copy Model Element        | copyModelElement                    |                       |                        |
| left Panel Element        | ModelLink__Container                |                       | yes                    |
| memory Indicator Container| MemoryIndicator-module__Container   |                       | yes                    |
| folder Count              | FoldersItemCard-module__CountModels |                       | yes                    |
| user Menu                 | UserMenu__userMenu                  |                       | yes                    |
| upper Left Cell           | TopLeftCell                         |                       |                        |
| import Manager List       | ImportManager_ListColumn            |                       |                        |
| modal Import Zone         | ImportManager__DnDZone              |                       |                        |
| import Manager Item       | ImportManager_ListColumn            |                       | yes                    |
| calendar Day Number       |                                     | day                   | yes                    |
| selection Body Layout     | GridSelectionBodyLayout             |                       |                        |
| selection Cols Layout     | GridSelectionColsLayout             |                       |                        |
| selection Rows Layout     | GridSelectionRowsLayout             |                       |                        |
| selection Left Top Layout | GridSelectionLeftTopLayout          |                       |                        |
| count Clusters            | Input__inputElement                 |                       |                        |
| thumb Inner               | RangeSlider-module__ThumbInner      |                       | yes                    |
| modal Search Input        | CreateModuleDialogBasicTab-module__SearchInput |            |                        |
| optimizer Input           | OptimizerTab-module__FormulaLine    |                       | yes                    |
| clear Result Search       | FilterInput__ClearButtonIcon        |                       |                        |
| scroller                  | scrollContainer , ScrollContainer , scrollContainer , ScrollContainer |   |          |
|                           | SelectBox__values , rc-dropdown-menu-vertical , ListElements-module__Content |   |   |
| basic Tab Card Setting    | BasicTabCardSetting                 |                       |                        |
| advanced Tab Card Setting | AdvancedTabCardSetting              |                       |                        |
| footer Copyright          | MainTabs__FooterCopyright           |                       |                        |
| grid Counter              | GridCounter                         |                       |                        |
| grid Counter Date         | GridCounterLastSyncDate             |                       |                        |
| grid Counter Count        | GridCounterCount                    |                       | yes                    |
| grid Counter Average      | GridCounterAverage                  |                       | yes                    |
| grid Counter Summ         | GridCounterSumm                     |                       | yes                    |
| grid Counter Filled Cells Count | GridCounterFilledCellsCount   |                       | yes                    |
| tag Title Container       | TagsItem__Container                 |                       |                        |
| grid Comments Container   | GridComments__Container             |                       |                        |
| header Comments           | Contents-module__headerCommentsClose|                       |                        |
| text Area Card Editor     | ql-container ql-snow                |                       |                        |
| card Of Context Table     | recharts-responsive-container , MapWithObjects-module__Container | |                 |
|                           | ImagesWithObjects-module__Container |                       |                        |
| dashboard Card            | BaseCard__content , Cards__Card     |                       |                        |
| toolbar Textarea Card     | BaseCard__content , Cards__Card     |                       |                        |
| textarea Card Button      |                                     |                       | yes                    |
| markdown Card             | BaseCard__content , Markdown        |                       |                        |
| dashboard Card With Id Name |                                   | name , data-name      | yes                    |
| markdown Editor           | MarkdownEditor__MarkdownEditorTextarea |                    |                        |
| markdown Preview          | MarkdownEditor__MarkdownEditorHtml  |                       |                        |
| media File                | MediaFileItem__preview              |                       |                        |
| modal Media Files         | MediaFileItem__preview              |                       |                        |
| comment By User           | GridCommentsElement__Container , GridCommentsElement__Info  |  | yes                  |
| zoom Slider               | ZoomSlider                          |                       |                        |
| main Tabs                 | MainTabs__Container                 |                       |                        |
| chart Scroll Conteiner    | ChartsDialog__config                |                       |                        |
| chart Tooltip             | recharts-tooltip-item , HoverInfo__HoverInfo , |            | yes                    |
|                           | FunnelChart__tooltip , ChartTooltip-module__Container |     |                        |
| zone Size Card            | react-resizable-handle              |                       |                        |
| grid Container            | Grid__GridScrollNode                |                       |                        |
| list Elements             | ListElements-module__Container      |                       |                        |
| list Element              | ListElements-module__Element        |                       | yes                    |
| progress Bar              | ProgressBar__Button                 |                       |                        |
| field                     | Fields__InputContainer              |                       | yes                    |
| target Formula Line       | TargetFormulaLine                   |                       |                        |
| variables Formula Line    | VariablesFormulaLine                |                       |                        |
| variables Formula Line Resizier | VariablesFormulaLineResizier  |                       |                        |
| constraints Formula Line  | ConstraintsFormulaLine              |                       |                        |
| dimensions Container      |                                     | data-name             | yes                    |
| header Folders Item       | Header__HeaderFoldersItem           |                       | yes                    |
| Input Confirm Delete Model Name | HeconfirmedText               |                       |                        |
| input New Model Name      | newModelName                        |                       |                        |
| input New Folder Name     | newFolderName                       |                       |                        |
| input                     | newFolderName                       | input , textarea - attr name | yes             |
| checkbox                  |                                     | checkbox              | yes                    |
| dropdown                  | dropdown                            |                       | yes                    |
| dropdown Option           |                                     |                       | yes                    |
| radio Button              |                                     | radio-button          | yes                    |
| grid                      | GridRootContainer                   |                       |                        |
| grid Error Info           | GridErrorInfo__Container            |                       |                        |
| col Headers Container     | ColHeaders                          |                       |                        |
| row Headers Container     | RowHeaders                          |                       |                        |
| cells Container           | Cells                               |                       |                        |
| grid In Dom               | ColHeaders , RowHeaders , Cells , TopLeftCell |             |                        |
| kanban In Dom             | CategoryContainer , CategoryTitle , WorkflowCard |          |                        |
| grid Cells By Selection   | GridSelection__Selected             |                       | yes                    |
| row Headers Range         | GridSelection__Selected             |                       | yes                    |
| col Headers Range         | GridSelection__Selected             |                       | yes                    |
| grid Cell                 | ContentCell                         |                       | yes                    |
| grid Cell Error           | SubmissionErrorCell                 |                       | yes                    |
| cell Pre Editor           | PreEditContainer                    |                       |                        |
| grid Cell Editor          | GridCellEditor                      |                       |                        |
| row Header                | RowHeaderCell                       |                       |                        |
| col Header                | ColumnHeaderCell                    |                       |                        |
| update Cell               | SubmissionCell                      |                       |                        |
| update Header             | SubmissionCell                      |                       |                        |
| style Heading Zero Level In Row Header  | heading0               |                       |                        |
| Style Heading First Level In Row Header | heading1               |                       |                        |
| style Heading Second Level In Row Header| heading2               |                       |                        |
| style Heading Third Level In Row Header | heading3               |                       |                        |
| Style Summary First Level In Row Header | summary1               |                       |                        |
| Style Summary Second Level In Row Header| summary2               |                       |                        |
| Style Summary Third Level In Row Header | summary3               |                       |                        |
| style Summary In Col Header             | summary                |                       |                        |
| rows Selection Container   | GridSelection__Rows                 |                       |                        |
| cells Selection Container  | GridSelection__Body                 |                       |                        |
| cols Selection Container   | GridSelection__Cols                 |                       |                        |
| cell Comments Body Container | CellComments__Body                |                       |                        |
| selection Row Header       | GridSelectionRowsLayout             |                       | yes                    |
| selection Col Header       | GridSelectionColsLayout             |                       | yes                    |
| only Selection Row Header  | GridSelectionRowsLayout             |                       | yes                    |
| only Selection Col Header  | GridSelectionColsLayout             |                       | yes                    |
| selection Grid Cell        | GridSelectionBodyLayout             |                       | yes                    |
| commented Cell             | CellComments__hasCellComments       |                       | yes                    |
| only Selection Grid Cell   | GridSelectionBodyLayout             |                       | yes                    |
| selection Row Headers      | GridSelectionBodyLayout             |                       | yes                    |
| only Selection Row Headers | GridSelectionBodyLayout             |                       | yes                    |
| selection Col Headers      | GridSelectionColsLayout             |                       | yes                    |
| only Selection Col Headers | GridSelectionColsLayout             |                       | yes                    |
| selection Grid Cells       | GridSelectionBodyLayout             |                       | yes                    |
| only Selection Grid Cells  | GridSelectionBodyLayout             |                       | yes                    |
| color Swatch               | Color__swatch                       |                       | yes                    |
| color                      |                                     | title                 | yes                    |
| color Scheme               | ColorPalette                        | name , data-name      | yes                    |
| action For Object          | MapWithObjectsConfig-module__ObjectsItem , |                | yes                    |
|                            | ImagesWithObjectsConfig-module__ObjectsItem|                |                        |
| control Zoom               |                                     | title                 | yes                    |
| map Region                 | datamap-subunit                     |                       | yes                    |
| contents                   | Contents                            |                       |                        |
| functional Area            | Functional Area                     |                       | yes                    |
| functional Area Label      | FunctionalArea__label               |                       | yes                    |
| contents Element           | ElementLink__label                  |                       | yes                    |
| contents Element View      | Elements__view                      |                       | yes                    |
| card Of Dashboards         | BaseCard__content , GridTitle-module__Title |               | yes                    |
| button Card With Name      | BaseCard__content , ButtonCard__Container |                 | yes                    |
| contents Dialog            | ContentsDialog__Container           |                       |                        |
| active Section             | Elements__isCurrent                 |                       |                        |
| dashboard Contents Dialog  | HelpDashboardTab__Container         |                       |                        |
| dashboard Scroll Content   | DashboardScrollContent              |                       |                        |
| context Menu               | ContextMenu-module__Container , rc-dropdown-menu-submenu-popup | |                   |
| context Menu Element       | ContextMenu-module__Element         |                       | yes                    |
| header Menu                | HeaderMenu__Menu                    |                       |                        |
| header Menu Element        | HeaderMenu__MenuItem                |                       | yes                    |
| approximate Header Menu Element | HeaderMenu__ElementContainer   |                       | yes                    |
| parent Header Menu Element | HeaderMenu__MenuItem_parent         |                       | yes                    |
| child Header Menu Element  | HeaderMenu__MenuItem_child          |                       | yes                    |
| header Title               | HeaderNavigation-module__Container  |                       | yes                    |
| module Name                | CreateModuleDialogAdvancedTab-module__InputField |          |                        |
| conditional Formatting     | Input__input                        |                       | yes                    |
| media File Config          | MediaFileDialog__configItem         |                       | yes                    |
| grid Settings Input        | grid-settings                       |                       |                        |
| filters                    | filterDropDown                      |                       |                        |
| filter                     | filterDropDown                      |                       | yes                    |
| formula                    | FormulaLine__Container              |                       |                        |
| formula Apply Button       | FormulaSubmitBar__Button            |                       |                        |
| formula Line Item          | FormulaLine__Title , FormulaColumn__Title |                 | yes                    |
| field With Cell Value      | FormulaLine__Result                 |                       | yes                    |
| formula Input              | FormulaEditorInput                  |                       |                        |
| formula Submit Bar         | FormulaSubmitBar                    |                       |                        |
| view Manager Item          | ViewManagerElement-module__Item     |                       | yes                    |
| copy Data Element          | CopyDataDialog-module__MulticubesElement , |                | yes                    |
|                            | CopyDataDialog-module__ResolutionListCheckbox |             |                        |
| view Manager Rename Input  | ViewManagerElement-module__ItemInsideInput |                | yes                    |
| pivot Filters Section      | dropZone--pages                     |                       |                        |
| pivot Rows Section         | dropZone--rows                      |                       |                        |
| pivot Columns Section      | dropZone--cols                      |                       |                        |
| dnd Zone                   | dropZone                            | name                  | yes                    |
| dnd Element                | DndElement__Target                  |                       | yes                    |
| sub Menu Scroll List       | HeaderMenu__SubMenuScrollList       |                       | yes                    |
| kanban Dnd Zone            | axisLabels , dropZone               |                       | yes                    |
| kanban Scroll Content      | WorkflowKanban__ContainerScroll     |                       |                        |
| kanban Element             | WorkflowCard__CardContent           |                       | yes                    |
| conditional Formatting Element | ConditionalFormatting__Element_TitleCube |              | yes                    |
| header Of Move Dialog      | Header_Title                        |                       |                        |
| view Manager Item Dragger  | ViewManagerElement-module__ItemInsideDragger |              | yes                    |
| grid Title Toolbar         | GridTitle-module__Toolbar           |                       |                        |

[Инструкция поиска селекторов](../slectors/instructionSelector.md)

[Инструкция по добавлению нового селектора]()

[Оглавление](../README.md)