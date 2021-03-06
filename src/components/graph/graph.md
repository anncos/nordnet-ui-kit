The UI kit exports three themes for highcharts and a base theme for easy overriding as well as a RangeSelector component.

    const { data } = require('./data.js');

    const config = {
      // settings here will override default theme using deep merge.
      series: [{
        type: 'area',
        data: data,
        tooltip: {
          valueDecimals: 2
        },
      }]
    };

    function randomizeData([time, val]) {
      const value = Math.round(Math.random()) ? val + Math.random() : val - Math.random();
      return [time, value];
    }

    const configAlt = {
      // settings here will override default theme using deep merge.
      series: [{
        type: 'area',
        data: data,
        tooltip: {
          valueDecimals: 2
        },
      }, {
        type: 'area',
        data: data.map(randomizeData) ,
        tooltip: {
          valueDecimals: 2
        },
      }, {
        type: 'area',
        data: data.map(randomizeData) ,
        tooltip: {
          valueDecimals: 2
        },
      }]
    };

    <div>
      <Graph
        name="graph"
        variant="dark"
        config={ config }
      />

      <Graph
        name="graph"
        variant="muted"
        config={ config }
      />

      <Graph
        name="graph"
        variant="light"
        config={ configAlt }
      />
    </div>
