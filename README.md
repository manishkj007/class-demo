@RestController
@RequestMapping("/api")
public class CurveController {

    private final CurveService curveService;

    @Autowired
    public CurveController(CurveService curveService) {
        this.curveService = curveService;
    }

    @ApiOperation(value = "Get Curve by Date API endpoint")
    @RequestMapping(value = "/curve", method = RequestMethod.GET)
    public ResponseEntity<List<CurveData>> getCurveData(
            @RequestParam(name = "asofDate", required = true)
            @DateTimeFormat(pattern = "yyyy-MM-dd") Date asofDate,
            @RequestHeader("Authorization") String authHeader
    ) {
        // Extract Bearer token
        String token = authHeader.replace("Bearer ", "");

        List<CurveEntity> curveEntities = curveService.getCurves(asofDate, token);

        List<CurveData> curveList = new ArrayList<>();
        for (CurveEntity entity : curveEntities) {
            CurveData data = new CurveData();
            data.setEffectiveDate(entity.getEffectiveDate());
            data.setRate(entity.getGen_rate03());
            data.setInstrumentName(entity.getInstrument_name());
            curveList.add(data);
        }

        return ResponseEntity.ok(curveList);
    }
}





