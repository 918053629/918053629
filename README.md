- 👋 Hi, I’m @918053629

```javascript

function brushApiCall(opperation) {
    switch (opperation) {
      case 'next-segment':
        segmentationModule.setters.incrementActiveSegmentIndex(element);
        cornerstone.updateImage(element);
        break;
      case 'previous-segment':
        segmentationModule.setters.decrementActiveSegmentIndex(element);
        cornerstone.updateImage(element);
        break;
      case 'switch-labelmap':
        if (activeLabelmapIndex === 0) {
          activeLabelmapIndex = 1;
        } else {
          activeLabelmapIndex = 0;
        }

        segmentationModule.setters.activeLabelmapIndex(element, activeLabelmapIndex);

        const label = document.getElementById('active-label-map-label');
        label.innerHTML = 'Active Labelmap: ' + activeLabelmapIndex;

        cornerstone.updateImage(element);

        break;

      case 'toggle-segment-1':
        const visible = segmentationModule.setters.toggleSegmentVisibility(element, 1);

        console.log(visible);

        const visibilityLabel = document.getElementById(
          'toggle-segment-1-label'
        );
        visibilityLabel.innerHTML = visible ? 'visible' : 'hidden';

        cornerstone.updateImage(element);
        break;
      case 'calculate-segment-1-stats':
        segmentationModule.getters.labelmapStats(element, 1).then(result => {
          const statsLabel = document.getElementById(
            'calculate-segment-1-stats-label'
          );

          if (result) {
            statsLabel.innerHTML = `vol: ${
              Math.round(result.volume)
              } mm, mean: ${
              Math.round(result.mean)
              }, stdDev: ${
              Math.round(result.stdDev)
              }, min: ${
              Math.round(result.min)
              }, max: ${
              Math.round(result.max)
              }`;

          } else {
            statsLabel.innerHTML = 'No segment.'
          }

        })
        break;
      default:
        return;
    }
  }

```
